<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';

    onMount(() => {
      function handleKeyDown(event) {
        if (event.key === 'ArrowLeft') {
          goto('/thesis'); // Navigate to the about page on right arrow press
        }
        if (event.key === 'ArrowRight') {
          goto('/segment-structure'); // Navigate to the about page on right arrow press
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
        <h1>Source</h1>
    </div>

    <div id="video">
        <video src="JO_source-2.mp4" preload="auto" tabindex="0" playsinline controls></video>
    </div>

    <div class="content">
        <p>And the show very clearly attributes sources and information they are getting from which their arguments rest on.</p>

        <p>Last Week Tonight often relies on secondary sources, but in this episode, they actually did their own investigation and provided their own source.</p>
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