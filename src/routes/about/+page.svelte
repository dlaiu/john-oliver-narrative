<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
  
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
  
<h1>
    about page
</h1>
