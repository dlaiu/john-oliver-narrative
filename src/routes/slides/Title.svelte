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
        height: auto;
    }
</style>