<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
    import Ai2html from '$lib/Ai2html.svelte';

    let page = 0;

    // Function to handle key presses
    let handleKeydown = (event) => {
      const chart = document.getElementById('chart');
      const [noJoke, jokes] = chart.children;
      const para = document.getElementById('second');

      console.log(page) 
      switch(event.keyCode) {
          case 37: // Left arrow key
            page -= 1;

            if (page === -1) {
              goto('/source');
              break;
            } else if (page === 1) {
              noJoke.classList.add('hidden');
              jokes.classList.remove('hidden');
              break;
            } else if (page === 0) {
              noJoke.classList.remove('hidden');
              jokes.classList.add('hidden');
              break;
            }
          case 39: // Right arrow key
            page += 1;
            if (page === 2) {
              goto('/structure-visual');
            console.log('next page')
              break;
            } else if (page === 1) {
              noJoke.classList.add('hidden');
              jokes.classList.remove('hidden');
              para.classList.remove('hidden'); 
              break;
            } 
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
    <div id='chart'>
        <div>
            <Ai2html name="segmentNoJoke" description="The Structure of a John Oliver Video" />
        </div>
        <div class="hidden">
            <Ai2html name="segmentVisual" description="The Structure of a John Oliver Video" />
        </div>
    </div>


<div class="body">
    <div class="content">
        <p>This is the typical structure for a sub-segment of the episode.</p>

        <p id="second" class="hidden">But what makes it different is that every subsegment tends to be punctuated with a joke.</p>
    </div>
</div>




<style>
    .hidden {
      display: none;
    }


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
    }
  </style>