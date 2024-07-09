<script>
    import Slide from '$lib/Slide.svelte';
</script>

<Slide bgColor="#8db3cf">
    <div class="content">
        <p class="sticky">And no one can deny the impact the show has had on policy:</p>
        <img src="/JO_impact_1.png" alt="">
        <img src="/JO_impact_2.png" alt="">
        <img src="/JO_impact_3.png" alt="">

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


</style>