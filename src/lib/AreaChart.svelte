<!-- LineChart.svelte -->
<script>
    import { onMount, onDestroy } from 'svelte';
    import { AreaChart } from '@carbon/charts';
    import '@carbon/charts/styles.css';
    import '@carbon/charts/styles.min.css';

    let container;
    let chart;

    onMount(() => {
        const data = [
    { group: "Waste Volume", date: "2023-07-15T00:00Z", volume: 122732 },
    { group: "Waste Volume", date: "2023-08-05T00:00Z", volume: 125024 },
    { group: "Waste Volume", date: "2023-08-12T00:00Z", volume: 125801 },
    { group: "Waste Volume", date: "2023-08-26T00:00Z", volume: 126305 },
    { group: "Waste Volume", date: "2023-09-02T00:00Z", volume: 127455 },
    { group: "Waste Volume", date: "2023-09-09T00:00Z", volume: 126981 },
    { group: "Waste Volume", date: "2023-09-16T00:00Z", volume: 127503 },
    { group: "Waste Volume", date: "2023-09-23T00:00Z", volume: 128754 },
    { group: "Waste Volume", date: "2023-10-01T00:00Z", volume: 129206 },
    { group: "Waste Volume", date: "2023-10-07T00:00Z", volume: 130425 },
    { group: "Waste Volume", date: "2023-10-14T00:00Z", volume: 129906 },
    { group: "Waste Volume", date: "2023-10-21T00:00Z", volume: 131005 },
    { group: "Waste Volume", date: "2023-10-29T00:00Z", volume: 131848 },
    { group: "Waste Volume", date: "2023-11-04T00:00Z", volume: 132700 },
    { group: "Waste Volume", date: "2023-11-11T00:00Z", volume: 133580 },
    { group: "Waste Volume", date: "2023-11-18T00:00Z", volume: 134426 },
    { group: "Waste Volume", date: "2023-11-25T00:00Z", volume: 135301 },
    { group: "Waste Volume", date: "2023-12-02T00:00Z", volume: 135984 }
];





        const options = {
            axes: {
                bottom: {
                    title: "Date",
                    mapsTo: "date",
                    scaleType: "time"
                },
                left: {
                    title: "Volume in m3",
                    mapsTo: "volume",
                    scaleType: "linear"
                }
            },
            curve: 'curveMonotoneX', // This makes the line curve smoothly
            height: "400px", // Optional: you can set height directly in options if preferred
            toolbar: {
                enabled: false, // This disables the toolbar
            },
            legend: {
                enabled: false, // This hides the legend
            },
            color: {
                scale: {
                    'Waste Volume': '#cea282'
                }
            },
        };

        chart = new AreaChart(container, {
            data,
            options,
        });
    });

    // Clean up the chart instance when the component is destroyed

    onDestroy(() => {
        chart.dispose();
    });
</script>

<div class="parent-container">
    <div bind:this={container} class="chart-container"></div>
</div>

<style>
    .parent-container {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 40vh;
    }

    .chart-container {
        height: 400px;
        width: 950px;
    }
</style>