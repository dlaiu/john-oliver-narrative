<script>
    import Slide from '$lib/Slide.svelte';
    import { base } from '$app/paths';

</script>

<Slide bgColor="#8db3cf">
    <div class="content">
        <h1 id="headline">How John Oliver does good journalism while making you laugh</h1>
        <img id="hero" src="{base}/JO_portrait-screengrab.png" alt="">
    </div>
</Slide>

<style>

    .content {
        margin: auto;
        padding: 50px;
        /* max-width: 100%;
        width: 100%; */
    }

    #headline {
        font-size: 5em;
        color: #494949;
        text-align: left;
        font-weight: 500;
        /* text-shadow: 0 0 2px #000; */
    }

    #hero {
        max-width: 100%;
        height: 100%;
    }

    /* Desktop-specific styles */
    @media (min-width: 768px) {
        .content {
            padding: 50px; /* Increased padding for desktop */
            max-width: 800px; /* Optional: Limit content width for better readability */
            max-height: 600px; /* Optional: Limit content height for a balanced layout */
        }

        #headline {
            font-size: 2.5em; /* Larger font for desktop */
            text-align: center; /* Center headline */
            max-height: 10vh; /* Optional: Limit headline height for a balanced layout */
            max-width: 100%; /* Optional: Limit headline width for a balanced layout */ 
        }

        #hero {
            max-width: 600px; /* Optional: Limit image width for a balanced layout */
            margin: 0 auto; /* Center image */
            display: block; /* Ensure image is treated as a block element */
            max-height: 30vh;
            
        }
    }
</style>