<script>
    import Slide from '$lib/Slide.svelte';
	import JokesCombined from '../../ai2html/jokesCombined.svelte';

</script>

<Slide bgColor="#8db3cf">
    <div class="content">
        
        <p class="sticky">So maybe that's the key to saving journalism.</p>
        <JokesCombined />    
        <p class="sticky">Make a point while making your audience laugh.</p>
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

    .sticky {   
        top: 0;
        background-color: #f1f1f14e;
        /* border: 1px black solid; */
        padding: 50px;
        font-size: 4em;
        color: #494949;
    }


</style>