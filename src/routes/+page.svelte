<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
  
    onMount(() => {
      function handleKeyDown(event) {
        if (event.key === 'ArrowRight') {
          goto('/structure-visual'); // Navigate to the about page on right arrow press
        }
      }
  
      window.addEventListener('keydown', handleKeyDown);
      return () => {
        window.removeEventListener('keydown', handleKeyDown);
      };
    });
</script>

  
<div class="header with-video-bg">
    <div class="video-background">
        <video src="JO_intro.mp4" preload="auto" tabindex="0" playsinline autoplay loop muted></video>
    </div>
    <div class="headline">
        <h1>The Structure <br/> of a <br/> John Oliver Video</h1>
    </div>
</div>
  
<style>
    .with-video-bg {
        /* position: relative;
        background-size: cover;
        margin-bottom: 2em; */

        /* Center everything inside */
        min-height: 70svh;
        display: flex;
        justify-content: center;
        align-items: center;

        /* White text with a shadow */
        color: white;
        text-shadow: 0px 0px 30px black,
            0px 0px 10px rgba(0, 0, 0, 0.5);



    }

    .video-background {
        position: absolute;
        top: 0;
        width: 100%;
        height: 100%;
        z-index: -1;
    }

    .video-background video {
        object-fit: cover;
        width: 100%;
        height: 100%;
    }

    .headline {
        text-align: center;
        padding: 2em;
        background: rgba(0, 0, 0, 0.5);
        border-radius: 10px;
        font-size: x-large;
    }
</style>