<script>
    import Slide from '$lib/Slide.svelte';
	import JokesCombined from '../../ai2html/jokesCombined.svelte';
    import { base } from '$app/paths';

</script>

<Slide bgColor="#8db3cf" bgImage="{base}/Paper-Texture-7.jpg" bgOpacity="0.2">
    <p class="sticky">This is a map of the different sections across the episode.</p>
    <JokesCombined maxHeight="300px"/>    
    <p class="sticky fragment fade-in">This is how John Oliver tricks you into consuming journalism.</p>
    
</Slide>

<style>

    .content {
        flex: auto;
        align-items: center;
        margin: auto;
        padding: 50px;
        /* width: 100%; */
        max-height: 30vh;
    }
    
    /* #hero {
        width: 125%;
    } */

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
            max-height: 30vh; /* Optional: Limit content height for a balanced layout */
            justify-self: center;
            margin:0;
        }

        .sticky {
            font-size: 1.8em;
        }

    }

</style>