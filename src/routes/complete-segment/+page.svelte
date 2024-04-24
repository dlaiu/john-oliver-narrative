<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';

    onMount(() => {
      function handleKeyDown(event) {
        if (event.key === 'ArrowLeft') {
          goto('/structure-visual'); // Navigate to the about page on right arrow press
        }

        if (event.key === 'ArrowRight') {
        //   goto('/thesis'); // Navigate to the about page on right arrow press
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
        <h1><span class="point">Point</span> / <span class="source"> Source </span> / <span class="joke">Joke</span></h1>
    </div>

    <div id="video">
        <video src="complete-segment.mp4" preload="auto" tabindex="0" playsinline controls></video>
    </div>
    
    <div class="content">
        <p>Here's a complete example of an entire subsegment in action.</p>

    </div>

</body>

<style>
     body {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .point {
        background-color: #dbcdf0;
    }

    .source {
        background-color: #faedcb;
    }

    .joke {
        background-color: #f0d6db;
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
        box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.2);
    }

    h1 {
        align-self: center;
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