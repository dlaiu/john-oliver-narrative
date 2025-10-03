<script>
    import Slide from '$lib/Slide.svelte';
    import { base } from '$app/paths';
</script>

<Slide bgColor="#8db3cf" bgImage="{base}/Paper-Texture-7.jpg" bgOpacity="0.2">
    <div class="content">
        <p class="sticky">And no one can deny the impact the show has had on policy:</p>
        <img src="{base}/JO_impact_1.png" alt="">
        <img src="{base}/JO_impact_2.png" alt="">
        <img src="{base}/JO_impact_3.png" alt="">

    </div>

</Slide>

<style>

    .content {
        flex: auto;
        align-items: center;
        margin: auto;
        padding: 50px;
        /* width: 100%; */
    }
    
    /* #hero {
        width: 125%;
    } */

    img {
        width: 100%;
        
    }

    .sticky {   
        top: 0;
        background-color: #f1f1f14e;
        /* border: 1px black solid; */
        padding: 50px;
        font-size: 4em;
        color: #494949;
    }

    @media (min-width: 768px) {
        .content {
            padding: 50px; /* Increased padding for desktop */
            max-width: 800px; /* Optional: Limit content width for better readability */
            max-height: 600px; /* Optional: Limit content height for a balanced layout */
        }

        .sticky {
            font-size: 1.7em;
            max-width: 30vw;
            justify-self: center;
        }

        img {
            max-width: 330px; /* Optional: Limit image width for a balanced layout */
            margin: 1.5em auto; /* Center image */
            display: block; /* Ensure image is treated as a block element */
            /* max-height: 40vh; */
            
        }
    }

</style>