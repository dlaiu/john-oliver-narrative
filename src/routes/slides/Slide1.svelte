<script>
    import Slide from '$lib/Slide.svelte';
    import { base } from '$app/paths';

</script>

<Slide bgColor="#8db3cf" bgImage="{base}/Paper-Texture-7.jpg" bgOpacity="0.2">
    <div class="content">
        <p class="sticky">This is John Oliver.</p>
        <div class="video-container">
            <video id="hero" data-src="{base}/JO_joke_mobile.mp4" preload="auto" data-autoplay controls muted></video>
            <img src="{base}/scanlines-fade.png" alt="" class="scanlines-overlay" />
        </div>
        <!-- <img id="hero" src="/JO_portrait-screengrab.png" alt=""> -->
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
        display: block;
        object-fit: contain;
    }

    #hero::-webkit-media-controls-panel {
        opacity: 0;
        transition: opacity 0.3s ease;
    }

    #hero:hover::-webkit-media-controls-panel {
        opacity: 1;
    }

    /* Firefox */
    #hero {
        --controls-opacity: 0;
    }

    #hero:hover {
        --controls-opacity: 1;
    }

    .video-container {
        position: relative;
        width: fit-content;
        height: auto;
        display: inline-block;
        max-width: 100%;
    }

    .scanlines-overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        object-fit: cover;
        z-index: 1;
        opacity: 0.35;
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
            max-width: 600px; /* Optional: Limit image width for a balanced layout */
            margin: 0 auto; /* Center image */
            display: block; /* Ensure image is treated as a block element */
            max-height: 40vh;
            
        }
    }
</style>