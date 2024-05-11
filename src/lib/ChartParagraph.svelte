<script>
    export let language = 'fr';
    $: console.log("Current language:", language);
</script>

<div class="container bx--type-body-long-02">
    <h3 class=" container bx--type-beta-02">
        {#if language === 'fr'}
        Le changement de volume du stock
        {:else}
        Change in the Stock Volume
        {/if}
    </h3>
    <p>
        {#if language === 'fr'}    
        Entre juillet et décembre 2023, j'ai réalisé des prises de vue hebdomadaires en 
        360 degrés du stock de déchets à l'aide d'un drone. Ces images ont été utilisées 
        pour générer des modèles 3D et des modèles d'élévation numérique par photogrammétrie, 
        permettant ainsi de mesurer le volume du stock. Comme vous pouvez le 
        voir sur le graphique ci-dessous, le volume du stock est passé de 122 732 m³ le 
        15 juillet à 135 984 m³ le 2 décembre 2023, illustrant une augmentation significative 
        sur cette période. 
        {:else}
        Between July and December 2023, I conducted weekly 360-degree drone footage of the waste stockpile. These images were used to generate 3D models and digital elevation models through photogrammetry, allowing the volume of the stockpile to be measured. As you can see in the chart below, the volume of the stockpile increased from 122,732 m³ on July 15 to 135,984 m³ on December 2, 2023, showing a significant increase over this period.
        {/if}
    </p>
    </div>
    
        <style>
           .container {
                max-width: 1000px;
                margin: 50px auto;
           }
           
           p, h3 {
        font-size: 1.4em;
        line-height: 1.5em;
        margin: 0 0 1em 0;
        padding: 0 20px; /* Padding inside paragraphs for better text alignment */
    }

            h3 {
                font-weight: bold; /* Ensuring headers are bold */
            }

        /* Media Queries for Responsive Adjustments */
        @media (max-width: 768px) {
            .container, p, h3 {
            margin: 20px auto; /* Slightly smaller margin on smaller screens */
            font-size: 1.2em; /* Adjust font size for readability */
        }
        
    }

    @media (max-width: 600px) {
        p, h3 {
            font-size: 1em; /* Smaller font size for very small devices */
            margin: 10px auto; /* Adjust margins to fit smaller screens */
        }
    }
        </style>