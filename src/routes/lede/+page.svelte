<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';

    onMount(() => {
      function handleKeyDown(event) {
        if (event.key === 'ArrowLeft') {
          goto('/structure-visual'); // Navigate to the about page on right arrow press
        }

        if (event.key === 'ArrowRight') {
          goto('/thesis'); // Navigate to the about page on right arrow press
        }
      }
  
      window.addEventListener('keydown', handleKeyDown);
      return () => {
        window.removeEventListener('keydown', handleKeyDown);
      };
    });
</script>

<body>
    <h1>Lede</h1>

    <div id="video">
        <video src="JO_lede.mp4" preload="auto" tabindex="0" playsinline controls></video>
    </div>

    <p>lorem ipsum</p>
</body>

<style>
    body {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    #video {
        width: 80%;
        align-self: center;
    }

    video {
        object-fit: cover;
        width: 100%;
    }

    h1 {
        align-self: center;
    }
</style>