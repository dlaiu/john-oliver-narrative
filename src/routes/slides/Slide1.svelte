<script>
    import Slide from '$lib/Slide.svelte';
    import { base } from '$app/paths';

</script>

<Slide bgColor="#8db3cf">
    <div class="content">
        <p class="sticky">This is John Oliver.</p>
        <video id="hero" data-src="{base}/JO_joke_mobile.mp4" preload="auto" data-autoplay></video>
        <!-- <img id="hero" src="/JO_portrait-screengrab.png" alt=""> -->
    </div>
</Slide>

<style>

    .content {
        margin: auto;
        padding: 50px;
    }

    #hero {
        width: 80%;
        height: auto;
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