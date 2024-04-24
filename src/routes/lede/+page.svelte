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

    <div class="title">
        <h1>Lede</h1>
    </div>

    <div id="video">
        <video src="JO_lede.mp4" preload="auto" tabindex="0" playsinline controls></video>
    </div>

    <div class="content">
        <p>For example, his episode always start out with "We're going to start with out main story tonight, which concers XYZ."</p>

        <p>This functions as a very clear lede to signpost not only the topic of the story, but also to continue to capture the viewer's attention.</p>
    </div>



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
        margin: 20px;
    }

    video {
        object-fit: cover;
        width: 100%;
        border-radius: 10px;
    }

    h1 {
        align-self: center;
        background-color: #c9e4de;
    }

    .content {
        width: 640px;
        align-self: center;
        font-family: Roboto, sans-serif;
    }

    .title {
        align-self: center;
        font-family: Roboto, sans-serif;
    }
</style>