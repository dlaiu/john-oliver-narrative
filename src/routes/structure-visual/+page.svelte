<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
	  import Scroller from './Scroller.svelte';

    onMount(() => {
      function handleKeyDown(event) {
        if (event.key === 'ArrowLeft') {
          goto('/'); // Navigate to the about page on right arrow press
        }
      }
  
      window.addEventListener('keydown', handleKeyDown);
      return () => {
        window.removeEventListener('keydown', handleKeyDown);
      };
    });

</script>

<!-- <div id='chart'>
  <Ai2html name="structureChart" description="The Structure of a John Oliver Video" />
</div> -->

<Scroller />