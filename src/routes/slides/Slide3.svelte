<script>
    import Slide from '$lib/Slide.svelte';
    let title;

</script>

<Slide bgColor="#8db3cf">
    <div class="content">
        <div class="r-stack">
            <p class="sticky fragment fade-out">He has consistently insisted that his show isn't journalism.</p>
            <p class="sticky fragment fade-in">I disagree.</p>
        </div>
        <img id="hero" src="/JO_not-journalism_screengrab.png" alt="">
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
</style>