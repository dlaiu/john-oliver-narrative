<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
	  import Scroller from './Scroller.svelte';
    import Ai2html from '$lib/Ai2html.svelte';

    let page = 0;

    // Function to handle key presses
    let handleKeydown = (event) => {
      // const chart = document.getElementById('chart');
      // const [structure, jokes] = chart.children;

      // console.log(chart)

      // console.log(page) 
      switch(event.keyCode) {
          case 37: // Left arrow key
            // page -= 1;
            goto('/segment-structure');
            break;
            // if (page === -1) {
            //   goto('/segment-structure');
            //   break;
            // } else if (page === 1) {
            //   structure.classList.add('hidden');
            //   jokes.classList.remove('hidden');
            //   break;
            // } else if (page === 0) {
            //   structure.classList.remove('hidden');
            //   jokes.classList.add('hidden');
            //   break;
            // }
          case 39: // Right arrow key
            goto('/complete-segment');
            break;
            // page += 1;
            // if (page >= 2) {
            //   goto('/lede');
            //   break;
            // } else if (page === 1) {
            //   structure.classList.add('hidden');
            //   jokes.classList.remove('hidden');
            //   break;
            // } 
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
  <Ai2html name="jokesCombined" description="The Structure of a John Oliver Video with jokes" />
  <!-- <div id='chart'>
    <div>
      <Ai2html name="structureChart" description="The Structure of a John Oliver Video" />
    </div>
    <div class="hidden">
      <Ai2html name="jokesCombined" description="The Structure of a John Oliver Video with jokes" />
    </div>
  </div> -->

  <div class="body">
    <p> And this structure is repeated throughout the episode, with jokes punctuated at the end of every sub-segment. </p>
  </div>
</body>



<!-- <Scroller /> -->

<style>
  .hidden {
    display: none;
  }

  /* #chart {
    max-height: 60%;
  } */


  .content {
        width: 640px;
        align-self: center;
        font-family: Roboto, sans-serif;
    }

  .body {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      font-family: Roboto, sans-serif;

  }
    
</style>