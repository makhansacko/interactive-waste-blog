<svelte:head>
  {#each images as image (image)}
    <link rel="preload" href="{image}" as="image">
  {/each}
  {#each imagesProfile as image (image)}
    <link rel="preload" href="{image}" as="image">
  {/each}
</svelte:head>

<script>
   import { Slider, Button } from 'carbon-components-svelte';
   import { onDestroy } from 'svelte';

   let sliderValue = 0;
   let playing = false;
    let intervalId;

    const images = [
        'July 15.png',
        'August 5.png',
        'August 12.png',
        'August 26.png',
        'September 2.png',
        'September 9.png',
        'September 16.png',
        'September 23.png',
        'October 1.png',
        'October 7.png',
        'October 14.png',
        'October 21.png',
        'October 29.png',
        'November 4.png',
        'November 11.png',
        'November 18.png',
        'November 25.png',
        'December 2.png',
    ];

    const imagesProfile = [
        'July 15_profil.png',
        'August 5_profil.png',
        'August 12_profil.png',
        'August 26_profil.png',
        'September 2_profil.png',
        'September 9_profil.png',
        'September 16_profil.png',
        'September 23_profil.png',
        'October 1_profil.png',
        'October 7_profil.png',
        'October 14_profil.png',
        'October 21_profil.png',
        'October 29_profil.png',
        'November 4_profil.png',
        'November 11_profil.png',
        'November 18_profil.png',
        'November 25_profil.png',
        'December 2_profil.png',
    ];
    $: imageMainSource = images[sliderValue];
    $: imageProfileSource = imagesProfile[sliderValue];
    $: maxIndex = images.length - 1;

    function togglePlay() {
        playing = !playing;
        if (playing) {
            startAnimation();
        } else {
            stopAnimation();
        }
    }

    function startAnimation() {
        stopAnimation();
        intervalId = setInterval(() => {
            sliderValue = (sliderValue + 1) % images.length;
        }, 400); // Change images every second
    }

    function stopAnimation() {
        if (intervalId) {
            clearInterval(intervalId);
            intervalId = null;
        }
    }

    onDestroy(() => {
        stopAnimation();
    });
</script>

<div class="container">
    <div class="images-row">
        <div class="image-container">
            <img src={imageMainSource} alt="Main view">
        </div>
        <div class="image-container">
            <img src={imageProfileSource} alt="Profile view">
        </div>
        </div>

        
        <Slider
        bind:value={sliderValue}
            min={0}
            max={maxIndex}
            step={1}
            labelText={images[sliderValue].replace('.png', '')}
            hideTextInput={false}
        />

        <Button kind="secondary" on:click={togglePlay}>{playing ? 'Pause' : 'Play'}</Button>   
</div>

<style>
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 20px;
        border: 0.5px solid #000;
        margin: 20px;
        width: 95%;
    }

    .images-row {
        display: flex;
        justify-content: space-around;
        width: 100%;
    }

    .image-container {
        flex: 1;
        padding: 10px;
        margin: 10px;
        border: 1px solid #ccc;
        display: flex;
        justify-content: center;
        align-items: center;
        max-width: 80%; /* Adjust size to allow two images side by side */
    }
    :global(.bx--slider) {
        width: 100% !important; /* Ensure this overrides any existing styles */
    }

    :global(.bx--slider__track) {
        background-color: #cea282!important; /* Ensure this overrides */
    }

    :global(.bx--slider__thumb) {
        background-color: #0a466b !important; /* Ensure this overrides */
    }
    img {
        max-width: 100%; /* Ensures the image scales down to fit the container */
        height: auto; /* Keeps the aspect ratio */
    }

    /* Media Queries for Responsive Adjustments */
    @media (max-width: 480px) {
        .container {
            padding: 5px; /* Even less padding for very small screens */
            margin: 5px; /* Less margin for very small screens */
        }

        .images-row {
            flex-direction: column; /* Ensure vertical stacking at very small widths */
        }

        .image-container {
            margin: 2px; /* Minimize margin to use space efficiently */
            padding: 2px; /* Minimize padding to use space efficiently */
        }
    }
</style>
