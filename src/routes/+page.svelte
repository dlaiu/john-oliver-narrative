<script>
    import { onMount } from 'svelte';
    import { goto } from '$app/navigation';
  
    onMount(() => {
      function handleKeyDown(event) {
        if (event.key === 'ArrowRight') {
          goto('/story-structure'); // Navigate to the about page on right arrow press
        }
      }
  
      window.addEventListener('keydown', handleKeyDown);
      return () => {
        window.removeEventListener('keydown', handleKeyDown);
      };
    });
</script>

<body>
    <div class="header with-video-bg">
        <div class="video-background">
            <video src="JO_intro.mp4" preload="auto" tabindex="0" playsinline autoplay loop muted></video>
        </div>
        <div class="headline">
            <h1>How John Oliver combines <br/> Journalism and Comedy</h1>
        </div>
    </div>

    <div class="content"> 
        <div class="row">

            <div class="arrow-left">
                <img src="/left-arrow.png" width="80" height="80"> 
            </div>

            <div class="article">

                <div class="byline">
                    <strong><p>By <a href="https://dlaiu.github.io">Darryl Laiu</a></p></strong>
                </div>

                <p>Last Week Tonight with John Oliver needs no introduction. </p>

                <p>The show has been on air since 2014, and it has made a name for itself for its commentary and extravagant stunts. </p>
        
                <p>For example, in an episode this season, Oliver taunts Supreme Court Justice Clarence Thomas, offering him a $2 million moto corach and $1 million a year.</p>
        
                <p>It has also won countless awards in 10 years it has been on air (no but actually look at the <a href="https://en.wikipedia.org/wiki/List_of_awards_and_nominations_received_by_Last_Week_Tonight_with_John_Oliver">Wikipedia</a> entry).</p>
        
                <p>One thing that Oliver has done is to constantly denies being at all journalistic in his show. </p>
        
                <video src="JO_not-journalism.mp4" preload="auto" tabindex="0" playsinline controls></video>
        
                <p>But I want to argue that his show inherently follows a journalistic structure to make its points. And that what makes his show work so well is how he blends comedy into that strucutre.</p>
        
                <p>So let's break down how Oliver combines journalism and comedy in his show.</p>
        
                <p>Press left and right on your keyboard to navigate through the rest of this essay.</p>
            </div>

            <div class="arrow-right">
                <img src="/right-arrow.png" width="80" height="80"> 
            </div>

        </div>



    </div>

    
</body>

  

  
<style>
    body {
        /* display: flex;
        justify-content: center; */
        margin: 0;
        font-family: Arial, sans-serif;
    }

    .byline {
        margin-top: 40px;
    }

    .content {
        /* max-width: 650px; */
        margin: 0 auto;
        padding: 2em;
    }

    .content video {
        width: 100%;
        margin: 1em 0;
    }

    .row {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
    }

    .article {
        width: 640px;
    }

    .arrow-left {
        justify-self: center;
    }


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

    .header {
        margin: 30px;
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
        height: 80%;
    }

    .headline {
        text-align: center;
        padding: 2em;
        background: rgba(0, 0, 0, 0.5);
        border-radius: 10px;
        font-size: x-large;
    }
</style>