<script>
    import { onMount } from 'svelte';
    import mapboxgl from 'mapbox-gl';
    import 'mapbox-gl/dist/mapbox-gl.css';
    // @ts-ignore
    import * as d3 from 'd3';
    import * as THREE from 'three';
    // @ts-ignore
    import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader';

    let map;
    export let visible = false;
    export let index = 0;
    let data = [];
    let markers = []; // Array to store markers

    mapboxgl.accessToken = 'pk.eyJ1IjoibWFraGFuc2Fja28iLCJhIjoiY2xyNzdveXk1MmF2cjJtbmVtc2xmZ2g1NyJ9.OT8LQZf8KpKBm0HBK7Fpuw'

    // @ts-ignore
    onMount(async() => {
        
        map = new mapboxgl.Map({
            container: 'map',
            style: 'mapbox://styles/makhansacko/clvisej92019n01phcikyf88q',
            center: [-7.991421689638932, 12.6072221987258],
            pitch: 50,
            zoom: getZoomLevel(),
        });

        // Add your 3D model here
        const modelOrigin = [-7.990000, 12.611119];
        const modelAltitude = 0;
        const modelRotate = [Math.PI / 2, 0, 0];
        const modelAsMercatorCoordinate = mapboxgl.MercatorCoordinate.fromLngLat(modelOrigin, modelAltitude);
        const modelTransform = {
            translateX: modelAsMercatorCoordinate.x,
            translateY: modelAsMercatorCoordinate.y,
            translateZ: modelAsMercatorCoordinate.z,
            rotateX: modelRotate[0],
            rotateY: modelRotate[1],
            rotateZ: modelRotate[2],
            scale: modelAsMercatorCoordinate.meterInMercatorCoordinateUnits()
        };

        const customLayer = {
            id: '3d-model',
            type: 'custom',
            renderingMode: '3d',
            onAdd: function (map, gl) {
                this.camera = new THREE.Camera();
                this.scene = new THREE.Scene();

                const directionalLight = new THREE.DirectionalLight(0xffffff, 4.0);
                // @ts-ignore
                directionalLight.position.set(0, -70, 100).normalize();;
                this.scene.add(directionalLight);

                const directionalLight2 = new THREE.DirectionalLight(0xffffff, 4.0);
                // @ts-ignore
                directionalLight2.position.set(0, 70, 100).normalize();
                this.scene.add(directionalLight2);

                const loader = new GLTFLoader();
                loader.load(
                    'August 5.glb',
                    (gltf) => {
                        this.scene.add(gltf.scene);
                    }
                );
                this.map = map;
                this.renderer = new THREE.WebGLRenderer({
                    canvas: map.getCanvas(),
                    context: gl,
                    antialias: true
                });
                this.renderer.autoClear = false;
            },
            render: function (gl, matrix) {
                const rotationX = new THREE.Matrix4().makeRotationAxis(new THREE.Vector3(1, 0, 0), modelTransform.rotateX);
                const rotationY = new THREE.Matrix4().makeRotationAxis(new THREE.Vector3(0, 1, 0), modelTransform.rotateY);
                const rotationZ = new THREE.Matrix4().makeRotationAxis(new THREE.Vector3(0, 0, 1), modelTransform.rotateZ);
                const m = new THREE.Matrix4().fromArray(matrix);
                const l = new THREE.Matrix4()
                    .makeTranslation(modelTransform.translateX, modelTransform.translateY, modelTransform.translateZ)
                    .scale(new THREE.Vector3(modelTransform.scale, -modelTransform.scale, modelTransform.scale))
                    .multiply(rotationX)
                    .multiply(rotationY)
                    .multiply(rotationZ);
                this.camera.projectionMatrix = m.multiply(l);
                this.renderer.resetState();
                this.renderer.render(this.scene, this.camera);
                this.map.triggerRepaint();
            }
        };

        map.on('style.load', () => {
            map.addLayer(customLayer, 'waterway-label');
        });
 
        data = await d3.csv('/waste_stocks_2.csv');

        return () => { // Cleanup function when the component is destroyed

        map.remove(); // Ensure the map instance is removed
    };

    });

    function getZoomLevel() {
            const width = window.innerWidth;
            if (width < 480) {
                return 14; // Closer zoom for very small screens
            } else if (width < 768) {
                return 12; // Moderate zoom for small to medium screens
            } else {
                return 12; // Default zoom for larger screens
            }
        }

//Functions outside onMount
        function getColor(type) {
        switch (type) {
            case 'Anarchique':
                return '#cea282';
            case 'Autorisé':
                return '#388E3C';
        }
        }
        
        $: if (visible && index >= 1) {
            markers.forEach(marker => marker.remove());
            markers = [];

            data.forEach(function(d) {
                const marker = new mapboxgl.Marker({
                color: index >= 2 ? getColor(d.type) : '#0a466b',
                scale: 0.7
            })
                    .setLngLat([+d.longitude, +d.latitude])
                    .addTo(map);

                    markers.push(marker); // Store marker in array
            });
        } else if (visible && index === 0) {
        markers.forEach(marker => marker.remove());
        markers = [];
    }

        $: if (visible && index === 3) {
        map.flyTo({
            center: [-7.991421689638932, 12.6072221987258],
            zoom: 17,
            speed: 0.8, // make the flying slow
            curve: 1 // change the speed at which it zooms out
              });
             }
       
        $: if (visible && index <= 2) {
        map.flyTo({
        center: [-7.991421689638932, 12.6072221987258], // Original center
        zoom: getZoomLevel(), // Original zoom level
        speed: 0.8, // Speed of transition
        curve: 1 // Smoothness of transition
         });
        }

</script>
<div id="map" style="width: 100%; height: 100%;" class:hidden={!visible}></div>

<style>
    #map {
        width: 100%; /* Full width to ensure it takes up all available space */
        height: 60vh; /* Full height to ensure it takes up all available vertical space */
        position: relative; /* Position relative to allow absolute positioning inside */
    }

    /* Media Queries for handling different screen sizes */
    @media (max-width: 768px) {
        /* Adjusting map height on smaller devices to ensure visibility of other page content */
        #map {
            height: 50vh; /* Half of the viewport height */
        }
    }

    @media (max-width: 480px) {
        /* Further adjustments for very small screens */
        #map {
            height: 50vh; /* Slightly more vertical space than on tablets */
        }
    }
</style>
