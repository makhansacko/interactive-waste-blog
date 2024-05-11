<script>
    export let language = 'fr';
    $: console.log("Current language:", language);
</script>

<div class="container bx--type-body-long-02">
    <h3 class=" container bx--type-beta-02">
        {#if language === 'fr'}
        Vers un Bamako Plus Propre : Enjeux et 
        Solutions pour la Gestion Durable et Inclusive des Déchets
        {:else}
        Towards a Cleaner Bamako: Challenges and
        Solutions for Sustainable and Inclusive Waste Management
        {/if}
    </h3>
    <p>
        {#if language === 'fr'}
        Alors que Bamako s'étend, le nombre et le volume des dépôts de déchets de la ville 
        ne cessent de croître. Cette réalité soulève des questions critiques quant à l'efficacité 
        des politiques publiques actuelles, malgré leur objectif de réguler et d'améliorer 
        la gestion des déchets.
        {:else}
        As Bamako expands, the number and volume of the city's waste dumps continue to grow.
        This reality raises critical questions about the effectiveness of current public policies,
        despite their aim to regulate and improve waste management.
        {/if}
    </p>

        <p>
            {#if language === 'fr'}
            Quelles solutions durables à cette problématique?
            {:else}
            What sustainable solutions to this issue?
            {/if}
        </p>

        <p>
            {#if language === 'fr'}
            Dans un prochain article, en adoptant toujours une perspective systémique, 
            nous explorerons les politiques publiques nationales et internationales
            de gestion des déchets, les initiatives menées par les acteurs locaux et internationaux, 
            ainsi que les stratégies potentielles pour une gestion plus durable des déchets à 
            Bamako. Restez à l'écoute pour découvrir comment nous pouvons transformer 
            ces défis en opportunités pour l'avenir de la ville.
            {:else}
            In an upcoming article, always adopting a systemic perspective, we will explore
            national and international public policies for waste management, initiatives led by local
            and international actors, as well as potential strategies for more sustainable waste management in
            Bamako. Stay tuned to discover how we can transform these challenges into opportunities for the future of the city.
            {/if}
        </p>
    </div>
    
        <style>
           .container {
                max-width: 1000px;
                margin: 50px auto;
                padding-left: 20px;  /* Add left padding */
                padding-right: 20px; /* Add right padding */
           }
           
           p, h3 {
        font-size: 1.4em;
        line-height: 1.5em;
        margin: 0 0 1em 0;
        padding: 0 20px; /* Padding inside paragraphs for better text alignment */
            }

         h3 {
         font-weight: bold; /* Ensure headers are bold */
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