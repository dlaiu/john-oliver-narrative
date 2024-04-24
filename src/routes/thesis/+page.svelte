<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';

    onMount(() => {
      function handleKeyDown(event) {
        if (event.key === 'ArrowLeft') {
          goto('/lede'); // Navigate to the about page on right arrow press
        }

        if (event.key === 'ArrowRight') {
          goto('/source'); // Navigate to the about page on right arrow press
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
        <h1>Thesis</h1>
    </div>

    <div id="video">
        <video src="JO_source.mp4" preload="auto" tabindex="0" playsinline controls></video>
    </div>

    <div class="content">
        <p>His videos always have a very clearly stated thesis, functionally making it like a video essay.</p>
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
        box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.2);
    }

    h1 {
        align-self: center;
        background-color: #99aaa6;
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