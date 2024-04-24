<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
    import Ai2html from '$lib/Ai2html.svelte';

    let page = 0;

    // Function to handle key presses
    let handleKeydown = (event) => {
      switch(event.keyCode) {
          case 37: // Left arrow key
            goto('/');
            break;
          case 39: // Right arrow key
            goto('/lede');
            break;
        
        }    
  

    }

    // Setup event listener for keydown events
    onMount(() => {
        window.addEventListener('keydown', handleKeydown);
        return () => {
            window.removeEventListener('keydown', handleKeydown);
        };
    });    

</script>

<body>
    <div class="title">
        <h1>The Structure of the Episode</h1>
    </div>
    <div id='chart'>
        <div>
          <Ai2html name="structureChart" description="The Structure of a John Oliver Video" />
        </div>
    </div>
  <div class="row">
    <div class="legend">
      <img src="structure_legend.png" alt="Legend for the structure visual" height="400" width="400" />
    </div>  
    <div class="content">
        <p>These are the sections of the entire main segment of the episode of John Oliver referenced before.</p>

        <p>As you can see, the show is pretty rigorous in sourcing, and it does follow a pretty consistent structure when trying to make it's point.</p>
    </div>
  </div>
</body>



<!-- <Scroller /> -->

<style>
    .row {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    }

    .content{
    width: 50%;
    font-family: 'Roboto', sans-serif;
    }

    h1 {
        align-self: center;
    }

    .title {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .body{
        font-family: 'Roboto', sans-serif;
    }
</style>