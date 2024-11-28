<script>
    import Slide from '$lib/Slide.svelte';
    import { base } from '$app/paths';

</script>

<Slide bgColor="#8db3cf">
    <div class="content">
        <div class="r-stack">
            <p class="sticky fragment fade-out">He has consistently insisted that his show isn't journalism.</p>
            <p class="sticky fragment fade-in">I disagree.</p>
        </div>
        <img id="hero" src="{base}/JO_not-journalism_screengrab.png" alt="">
    </div>
</Slide>

<style>

    .content {
        margin: auto;
        padding: 50px;
    }
    
    #hero {
        width: 100%;
        height: auto;
        margin-top: 50px;
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
            font-size: 2em;
            max-width: 30vw;
            justify-self: center;
        }

        #hero {
            max-width: 330px; /* Optional: Limit image width for a balanced layout */
            margin: 1.5em auto; /* Center image */
            display: block; /* Ensure image is treated as a block element */
            /* max-height: 40vh; */
            
        }
    }
</style>