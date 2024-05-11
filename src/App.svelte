<script>
	import Scroller from '@sveltejs/svelte-scroller/Scroller.svelte';
	import Introduction from './lib/Introduction.svelte';
	import MapComponent from './lib/MapComponent.svelte';
	import 'carbon-components/css/carbon-components.min.css';
	import ChartParagraph from './lib/ChartParagraph.svelte';
    import AreaChart from './lib/AreaChart.svelte';
    import ModelSlider from './lib/ModelSlider.svelte';
	import SliderParagraph from './lib/SliderParagraph.svelte';
	import Conclusion from './lib/Conclusion.svelte';
	import LanguageSwitch from './lib/LanguageSwitch.svelte';
	import Signature from './lib/Signature.svelte';
	import {onMount} from 'svelte';
	

	let count;
	let index;
	let offset;
	let progress;
	let top = 0;
	let threshold = 0.6;
	let bottom = 0.9;
	let language = 'fr';

	function handleLanguageChange(event) {
        language = event.detail;
		history.pushState({}, '', `?lang=${language}`);
    }

	onMount(() => {
    const urlParams = new URLSearchParams(window.location.search);
    const lang = urlParams.get('lang');
    if (lang) {
        language = lang;
    }
});

</script>

<div class="title-screen container bx--type-body-long-02">
    <LanguageSwitch on:languageChanged={handleLanguageChange}/>

	<h1>
		{#if language === 'fr'}
		Perspective systémique sur les déchets solides de la ville de Bamako<br>Partie 1: Focus 
		sur les stocks
		{:else}
		Systemic Perspective on Solid Waste in the City of Bamako<br>Part 1: Focus on Stocks
		{/if}
	</h1><br>
    <div class="mouse">
        <div class="wheel"></div>
    </div>
    <p>
		{#if language === 'fr'}
		Défiler vers le bas pour continuer
		{:else}
		Scroll down to continue
		{/if}
	</p>
</div>

	<div>
	<Introduction {language}/>
	</div>

	<Scroller
		{top}
		{threshold}
		{bottom}
		bind:count
		bind:index
		bind:offset
		bind:progress
	>
		<div slot="background" style="height: 100vh;">
		<MapComponent {index} visible={index >= 0 }/>
		</div>

		<div slot="foreground" class="foreground">
			<div class="spacer"></div>
			<section><p class="container bx--type-body-long-02 larger-text"> 
				{#if language === 'fr'}
				Avec une population de 4 227 569 
				habitants en 2022 (RGPH5), Bamako est la capitale et la plus grande ville du Mali. 
				Située sur le 
				fleuve Niger, près des rapides qui séparent les vallées du Niger supérieur et moyen, 
				elle se trouve dans la partie sud-ouest du pays.
				{:else}
				With a population of 4,227,569 in 2022 (RGPH5), Bamako is the capital and largest 
				city of Mali. Located on the Niger River, near the rapids that separate the upper 
				and middle Niger valleys, it is situated in the southwestern part of the country.
				{/if}
				</p></section>

			<section><p class="container bx--type-body-long-02 larger-text stocks">
				{#if language === 'fr'}
				Les données collectées 
				nous ont permis de cartographier 60 stocks de déchets solides repartis dans les différents 
				quartiers de Bamako. La taille et le volume de ces stocks varient mais comme mentionné
				plus haut, leur composition reste très similaires.
				{:else}
				The data collected allowed us to map 60 solid waste stocks distributed across various 
				neighborhoods of Bamako. The size and volume of these stocks vary, but as mentioned 
				earlier, their composition remains very similar.
				{/if}
			</p></section>
			<section>
				<p class="container bx--type-body-long-02 larger-text">
					{#if language === 'fr'}
					Ces stocks ou dépots de transit sont 
					categorisés principalement en deux types: anarchique et autorisé. On s'aperçoit que la 
					très grande majorité des stocks sont anarchiques, soit 85% des stocks cartographiés.
					{:else}
					These stocks or transit depots are mainly categorized into two types: anarchic and 
					authorized. It is observed that the vast majority of stocks are anarchic, 
					accounting for 85% of the mapped stocks.
					{/if}
					</p>
				{#if index >= 2}
                    <div id="legend">
                        <div class="bx--type-body-long-02 larger-text">
							<span style="background-color: #cea282; display: 
							inline-block; width: 10px; height: 10px; margin-right: 10px;">
							</span>
							{#if language === 'fr'}
							Anarchique
							{:else}
							Anarchic
							{/if}
						</div>
                        <div class="bx--type-body-long-02 larger-text">
							<span style="background-color: #388E3C; display: inline-block; 
							width: 10px; height: 10px; margin-right: 10px;">
						</span>
						{#if language === 'fr'}
						Autorisé
						{:else}
						Authorized
						{/if}
						</div>
                    </div>
                {/if}
			</section>
			<section><p class="container bx--type-body-long-02 larger-text">
				{#if language === 'fr'}
				Nous avons accordé une 
				attention particulière au dépôt de transit anarchique situé près de l'Université de 
				Bamako, également connu sous le nom de "la colline du savoir". Ce dépôt, qui s'étend 
				sur une superficie et une hauteur comparable à celle d'une colline, fait partie intégrante du 
				paysage urbain et académique de la ville depuis de nombreuses années. Comme illustré 
				sur la carte, ce site est situé à proximité immédiate de l'université, 
				avec les bâtiments universitaires visibles à droite du dépôt.
				{:else}
				We paid particular attention to the anarchic transit depot located near the 
				University of Bamako, also known as "the hill of knowledge". This depot, 
				which extends over an area and height comparable to that of a hill, has been 
				an integral part of the urban and academic landscape of the city for many years. 
				As illustrated on the map, this site is located in the immediate vicinity of 
				the university, with university buildings visible to the right of the depot.
				{/if}
			</p></section>
			<section><p class="container bx--type-body-long-02 larger-text">
				{#if language === 'fr'}
				Avec un flux constant de 
				déchets solides transportés par les GIE et charretiers individuels, comment évolue 
				le volume de ce stock au fil du temps ? Nous avons exploré cette question pour y 
				apporter une réponse.
				{:else}
				With a constant flow of solid waste transported by GIEs and individual carters,
				how does the volume of this stock change over time? We explored this question to
				provide an answer.
				{/if}
			</p></section>

		</div>
	</Scroller>

	<div class="bx--type-body-long-01">
	<ChartParagraph {language}/>
	</div>

	<div class="area-chart-container">
	<AreaChart/>
	</div>

	<div class="bx--type-body-long-01">
	<SliderParagraph {language}/>
	</div>

	<ModelSlider/>

	<Conclusion {language}/>

	<div>
	<img class= "smoky-waste" src='/smoking_waste.jpg' alt="Smoking waste">
	</div>

<Signature name= "Makhan Sacko" />

<style>
	.title-screen {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
        text-align: center;
		color: white;
		background-image: url('/Image_stock.jpg');
        background-size: cover; /* Cover the entire area of the title screen */
        background-position: center; /* Center the image */
		position: relative;
		z-index: 0;
    }

	.title-screen::before {
        content: '';
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background-color: rgba(0, 0, 0, 0.5); /* Semi-transparent black */
		z-index: -1;
    }

	.title-screen h1 {
		font-size: 2.5em; /* Increase the size */
        font-weight: bold; /* Make it bold */
    }

	.spacer {
		height: 50vh;
	}

	.larger-text {
		font-size: 1.4em;
	}

	.mouse {
        width: 20px;
        height: 35px;
        border: 2px solid black;
        border-radius: 10px;
        position: relative;
        display: inline-block;
        margin: 0 auto;
		border: 1px solid white;
    }

    .wheel {
        width: 3px;
        height: 5px;
        background: black;
        position: absolute;
        top: 10px;
        left: 50%;
        transform: translateX(-50%);
        animation: scroll 1s infinite;
		border: 1px solid white;
    }

    @keyframes scroll {
        0% { transform: translateX(-50%) translateY(0); }
        50% { transform: translateX(-50%) translateY(10px); }
        100% { transform: translateX(-50%) translateY(0); }
    }
	
	.foreground {
    padding: 0 0 0 70%;
  }

	[slot="background"] {
		font-size: 1.4em;
		overflow: hidden;
		padding: 1em;
	}
	
	[slot="foreground"] {
		width: 35%;
		padding: 5em;
	}
	
	[slot="foreground"] section {
		pointer-events: all;
        background-color: #455A64; /* Background color for better readability */
        color: white; /* Text color for contrast */
        padding: 10px 20px; /* Padding around text for better spacing */
        margin-bottom: 400px; /* Space between sections for clarity */
		width: auto; /* Use full width */
		max-width: 100%;
        box-sizing: border-box; /* Include padding in width calculation */
	}
	
	section {
		background-color: #455A64;
		color: white;
		padding: 1em;
		margin: 10px auto;
		max-width: none;
		width: auto;
	}

	section:last-of-type {
		margin-bottom: 10em;
		padding-bottom: 0;
	}

	#legend {
		padding-top: 1em;
	}
	.bx--type-body-long-01 {
    margin-top: 10em; /* Adjust this value as needed */
}
	.area-chart-container {
        padding-bottom: 10em;
		align-items: center;
		justify-content: center;
        height: 300px; /* Fixed height for consistency */
        width: 100%; /* Full width to use the space efficiently */
        max-width: 600px; /* Limiting max width for aesthetics */
	}

	.smoky-waste {
	display: block;
	width: 70%;
	margin: auto;
	}

	/* Media Queries for Responsive Adjustments */
    @media (max-width: 768px) {
        .title-screen h1 {
            font-size: 1.8em; /* Smaller font size for smaller screens */
        }

        .larger-text {
            font-size: 1.2em; /* Smaller text size for readability on smaller devices */
        }

		.foreground {
			width: 90%;
		}

        section {
            margin: 0 auto 20px; /* Reduced margin */
			width: 100%;
			margin: 0 auto 20px; /* Center and space sections */
			padding: 10px 15px;
        }
        }

        [slot="background"] {
            padding: 0.5em; /* Smaller padding for smaller screens */
        }

        .area-chart-container {
            max-width: 90%; /* More width allowed on smaller screens */
			margin-bottom: 7em;
        }

        .smoky-waste {
            width: 100%; /* Full width for better visibility */
        }

		[slot="foreground"] {
        padding-left: 10%; /* Minimal padding for small screens */
    	}

    	@media (max-width: 600px) {
        .title-screen h1 {
            font-size: 1.8em; /* Even smaller font size for very small devices */
        }

        .larger-text {
            font-size: 1em; /* Reduce font size for very small screens */
        }

        section {
            width: 90%;
        }

		.foreground {
			width: 90%;
		}
		
		[slot="foreground"] {
        padding-left: 10%; /* Minimal padding for small screens */
		margin-bottom: 400px;
    }
    }
</style>