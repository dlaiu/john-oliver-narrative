<script>
    import Slide from '$lib/Slide.svelte';
	import JokesCombined from '../../ai2html/jokesCombined.svelte';
    import { base } from '$app/paths';

</script>

<Slide bgColor="#8db3cf" bgImage="{base}/Paper-Texture-7.jpg" bgOpacity="0.2">
    <p class="sticky">So maybe that's the key to saving journalism.</p>
    <JokesCombined maxHeight="300px"/> 
    <p class="sticky">Make a point while making your audience laugh.</p>
    
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