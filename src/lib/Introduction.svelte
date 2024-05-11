<script>
    export let language = 'fr';
    $: console.log("Current language:", language);
</script>

<p class="container bx--type-body-long-02">
    {#if language === 'fr'}
    Plongez dans le système complexe de gestion 
    des déchets de Bamako, où chaque tas de déchets raconte une histoire de connexions, 
    de flux et de défis systémiques. Cette série de blogs explore comment les différents éléments du 
    système—les stocks de déchets, les acteurs impliqués, et les processus qu'ils 
    engagent—s'entrelacent pour façonner le paysage urbain et environnemental de la ville. Elle 
    explore aussi les pistes de solutions durables à la problématique.
    Dive into the complex waste management system of Bamako, where each pile of waste tells a 
    story of connections, flows, and systemic challenges. This blog series explores how the different 
    elements of the system—the waste stocks, the actors involved, and the processes they engage 
    in—interweave to shape the urban and environmental landscape of the city. It also explores 
    sustainable solutions to the issue.
    {:else}
    Dive into the complex waste management system of Bamako, where each pile of waste tells a story 
    of connections, flows, and systemic challenges. This blog series explores how the different elements 
    of the system—the waste stocks, the actors involved, and the processes they engage in—interweave to 
    shape the urban and environmental landscape of the city. It also explores sustainable solutions to 
    the issue.
    {/if}
</p>
    <p class="container bx--type-body-long-02">
    {#if language === 'fr'}    
    À Bamako, la gestion des déchets ne se limite pas à 
    l'élimination des ordures. Elle représente un réseau dynamique composé de producteurs de déchets, de groupements et associations 
    de pré-collecte, de transformateurs et de services de collecte. Chaque composant de ce système 
    influence et est influencé par les autres, créant un écosystème de gestion des déchets où les 
    actions de l'un affectent l'ensemble. Toutefois, des lacunes subsistent, notamment dans les 
    liens entre la transformation des déchets et les autres maillons, ce qui représente une opportunité 
    d'amélioration significative pour les communautés du district.
    {:else}
    In Bamako, waste management is not limited to the disposal of garbage. It represents a dynamic network composed of waste producers, pre-collection groups and associations, transformers, and collection services. Each component of this system influences and is influenced by the others, creating a waste management ecosystem where the actions of one affect the whole. However, gaps remain, particularly in the links between waste transformation and other elements, which represents a significant opportunity for improvement for the district's communities.
    {/if}
</p>

    <p class="container bx--type-body-long-02">
        {#if language === 'fr'}
        Ce blog vous invite à découvrir comment les montagnes de 
        déchets de Bamako, en particulier celles près de l'Université de Bamako, évoluent et s'accumulent.
        Nous utiliserons des images drone en 360 degrés et des modélisations 3D pour suivre l'évolution 
        de ces stocks, offrant un aperçu visuel du volume de déchets au fil du temps. Ces types de 
        visualisations servent non seulement à illustrer le problème, mais aussi à démontrer comment les diverses 
        interventions au sein du système peuvent conduire à des changements positifs.
        {:else}
        This blog invites you to discover how the mountains of waste in Bamako, especially those near the University of Bamako, evolve and accumulate. We will use 360-degree drone images and 3D modeling to track the evolution of these stocks, providing a visual insight into the volume of waste over time. These types of visualizations serve not only to illustrate the problem but also to demonstrate how various interventions within the system can lead to positive changes.
        {/if}
    </p>

    <h3 class=" container bx--type-beta-02">
        {#if language === 'fr'}
        Les déchets solides de Bamako
        {:else}
        Solid waste in Bamako
        {/if}
    </h3>
    <p class="container bx--type-body-long-02">
        {#if language === 'fr'}
        Les déchets dans le district se composent majoritairement 
        d'ordures ménagères, qui forment 99% des déchets, avec des proportions beaucoup plus faibles de 
        déchets hospitaliers (0,4%) et industriels (0,6%). Les ordures ménagères elles-mêmes sont 
        principalement constituées de poussière et matières fines (51%), de déchets végétaux et de restes 
        de cuisine (chacun à 17,5%), et d'autres types de déchets (13%). Malgré des variations dans les 
        volumes de déchets produits d'une commune à l'autre, liées aux tailles des populations ou à la 
        présence d'industries et de  marchés, la composition des déchets reste relativement constante 
        à travers les six communes du district (Source: rapport étude Tokten, 2019).
        {:else}
        Waste in the district consists mainly of household waste, which accounts for 99% of waste, with much smaller proportions of hospital waste (0.4%) and industrial waste (0.6%). Household waste itself is mainly composed of dust and fine materials (51%), vegetable waste and kitchen scraps (each at 17.5%), and other types of waste (13%). Despite variations in waste volumes produced from one municipality to another, related to population sizes or the presence of industries and markets, the composition of waste remains relatively constant across the six municipalities of the district (Source: Tokten study report, 2019).
        {/if}
    </p>

        <div class="img-container" id="repartition">
            <img class="repartition" src="repartitions_stock.png" alt="Stocks de déchets">
        </div>

<p class="container bx--type-body-long-02">
    {#if language === 'fr'}
    Au fil de notre exploration, nous avons collecté les données sur 
    les sites de stockage ou dépôts de transit de déchets, éparpillés à travers les quartiers de la ville. Ces 
    emplacements servent de points de chute où les équipes de pré-collecte déversent les déchets solides.
    {:else}
    Throughout our exploration, we collected data on waste storage sites or transit depots, scattered throughout the city's neighborhoods. These locations serve as drop-off points where pre-collection teams dump solid waste.
    {/if}
</p>

    <p class="container bx--type-body-long-02">
    {#if language === 'fr'}    
    La carte interactive ci-dessous présente la géolocalisation de ces stocks, en indiquant également le 
    type de chaque dépôt. La carte présente également le stock de déchets de l'Université de Bamako, qui
    est notre cas d'étude.
    {:else}
    The interactive map below shows the geolocation of these stocks, also indicating the type of each depot. The map also presents the waste stock of the University of Bamako, which is our case study.
    {/if}
    </p>


    <style>
    .container {
        max-width: 1000px;
        margin: 50px auto;
        padding-left: 20px;  /* Ensure padding doesn't affect centering */
        padding-right: 20px; /* Ensure padding doesn't affect centering */
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

    .img-container {
        display: flex;
        justify-content: center; /* Centers the child elements horizontally */
        align-items: center; /* Centers the child elements vertically, if needed */
        flex-direction: column; /* Stack children vertically */
    }

    .repartition {
        width: 50%; /* Relative size to its container, adjust as needed */
        height: auto; /* Maintain aspect ratio */
    }

    @media (max-width: 768px) {
        .container, p, h3 {
            margin: 20px auto; /* Slightly smaller margin on smaller screens */
            font-size: 1.2em; /* Adjust font size for readability */
        }

        .repartition {
            width: 100%; /* Use full width on smaller screens */
        }
    }

    @media (max-width: 600px) {
        p, h3 {
            font-size: 1em; /* Smaller font size for very small devices */
            margin: 10px auto; /* Adjust margins to fit smaller screens */
        }
    }
</style>