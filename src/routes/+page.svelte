<!-- <script>
    import { onMount } from 'svelte';

    // Sample data: array of messages to display
    let messages = ["Hello, World!", "Welcome to Svelte!", "Press the arrow keys!", "Enjoy coding!"];
    let currentIndex = 0;

    // Function to handle key presses
    function handleKeydown(event) {
        switch(event.keyCode) {
            case 37: // Left arrow key
                currentIndex = (currentIndex > 0) ? currentIndex - 1 : messages.length - 1;
                break;
            case 39: // Right arrow key
                currentIndex = (currentIndex < messages.length - 1) ? currentIndex + 1 : 0;
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

<style>
    main {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        font-size: 24px;
        text-align: center;
    }
</style>

<main>
    {messages[currentIndex]}
</main> -->


<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
  
    onMount(() => {
      function handleKeyDown(event) {
        if (event.key === 'ArrowRight') {
          goto('/about'); // Navigate to the about page on right arrow press
        }
      }
  
      window.addEventListener('keydown', handleKeyDown);
      return () => {
        window.removeEventListener('keydown', handleKeyDown);
      };
    });
  </script>
  
  <h1>Home Page</h1>
  <p>Press the right arrow key to go to the About page.</p>
  