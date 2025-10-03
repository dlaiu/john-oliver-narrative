<script>
    import Slide from '$lib/Slide.svelte';
    import { base } from '$app/paths';

</script>

<Slide bgColor="#8db3cf" bgImage="{base}/Paper-Texture-7.jpg" bgOpacity="0.2">
    <div class="content">
        <video id="hero" data-src="{base}/JO_joke_mobile.mp4" preload="auto" controls muted></video>
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

    .sticky {   
        top: 0;
        background-color: #f1f1f14e;
        /* border: 1px black solid; */
        padding: 50px;
        font-size: 4em;
        color: #494949;
    }
</style>