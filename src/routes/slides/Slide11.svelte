<script>
    import { base } from '$app/paths';
	import { browser } from '$app/environment';
	import Slide from '$lib/Slide.svelte';

	import { onMount, onDestroy } from 'svelte';
	let video;
	let captions = [];
	let subtitles = [];
	let durationPerWord = 0.35;
	let timeUpdateHandler;
	let slideElement; // Reference to this slide's DOM element

	onMount(() => {
		if (!browser) return;
		
		// Only select captions within this slide element
		captions = slideElement.querySelectorAll('.caption');

		console.log('Captions:', captions); // Verify captions are selected

		timeUpdateHandler = () => {
			const currentTime = video.currentTime;
			console.log('Current Time:', currentTime); // Verify video time updates

			captions.forEach((caption, captionIndex) => {
				const start = parseTime(caption.getAttribute('data-start'));
				console.log('Start Time:', start); // Verify start time parsing

				// Get the next caption's start time to determine end time
				const nextCaption = captions[captionIndex + 1];
				const end = nextCaption ? parseTime(nextCaption.getAttribute('data-start')) : video.duration;

				// Only highlight if current time is within this caption's timeframe
				if (currentTime >= start && currentTime < end) {
					const subtitles = caption.querySelectorAll('.subtitle');
					console.log('Subtitles:', subtitles); // Verify subtitles are selected

					subtitles.forEach((subtitle, index) => {
						const wordStart = start + index * durationPerWord;

						if (currentTime >= wordStart) {
							subtitle.classList.add('highlighted');
							subtitle.style.backgroundColor = '#FFADAD';
							console.log(`Adding is-visible to word ${index}`); // Log class addition
						} else {
							subtitle.classList.remove('highlighted');
							subtitle.style.backgroundColor = '';
						}
					});
				} else {
					// Remove highlighting from captions that are not currently active
					const subtitles = caption.querySelectorAll('.subtitle');
					subtitles.forEach((subtitle) => {
						subtitle.classList.remove('highlighted');
						subtitle.style.backgroundColor = '';
					});
				}
			});
		};

		if (video) {
			video.addEventListener('timeupdate', timeUpdateHandler);
		}
	});

	onDestroy(() => {
		if (!browser) return;
		
		if (video && timeUpdateHandler) {
			video.removeEventListener('timeupdate', timeUpdateHandler);
		}
		// Clean up highlighting only in this slide
		if (slideElement) {
			const allSubtitles = slideElement.querySelectorAll('.subtitle');
			allSubtitles.forEach((subtitle) => {
				subtitle.classList.remove('highlighted');
				subtitle.style.backgroundColor = '';
			});
		}
	});

	function parseTime(timeString) {
		const parts = timeString.split(':');
		const hours = parseInt(parts[0], 10);
		const minutes = parseInt(parts[1], 10);
		const seconds = parseInt(parts[2], 10);
		const frames = parseInt(parts[3], 10);
		return hours * 3600 + minutes * 60 + seconds + frames / 25;
	}
</script>

<Slide bgColor="#8db3cf" bgImage="{base}/Paper-Texture-7.jpg" bgOpacity="0.2">
    <div class="content" bind:this={slideElement}>
        <p class="sticky">He then uses the <span style="background-color:#FFADAD">joke</span> to puncutate the point he's trying to make.</p>

		<div class="video-container">
			<video bind:this={video} preload="auto" data-autoplay controls muted>
				<source src="{base}/JO_Joke_Landscape.mp4" type="video/mp4" />
			</video>
			<img src="{base}/scanlines-fade.png" alt="" class="scanlines-overlay" />
		</div>

        <p class="transcript">
            <span class="caption Point" data-start="00:20:53:16">But lawmakers shouldn't be learning how to perform executions  from one. That legislator then called in this guy, a  high school friend of his and criminal justice professor who put together a presentation  for the legislature in which he tried to prove the method  was painless by, for some reason, playing YouTube videos of kids  passing out from breathing helium.</span>
            <span class="caption Source" data-start="00:21:14:11">So this is a teenager that is breathing helium  to make their voice sound funny, but they're not really thinking that when they're breathing helium,  they're not breathing oxygen. And so she's trying to get as big a breath  as she can, and in a second,  she becomes hypoxic. So then they get back up and they're  giggling and laughing. Now, obviously,  there's a lot wrong with that.</span>
            <span class="caption Explanation" data-start="00:21:53:08">For starters, those kids are voluntarily  depriving themselves of oxygen, not trying to resist, which is what would  likely happen during an execution. So you can't really compare  the two scenarios. But since Oklahoma lawmakers  seem to respond</span>
            <span class="caption Joke" data-start="00:00:00:00">
                <span class="subtitle">well</span>
                <span class="subtitle">to</span>
                <span class="subtitle">videos</span>
                <span class="subtitle">of</span>
                <span class="subtitle">people</span>
                <span class="subtitle">on</span>
                <span class="subtitle">helium,</span>
                <span class="subtitle">allow</span>
                <span class="subtitle">me</span>
                <span class="subtitle">to</span>
                <span class="subtitle">address</span>
                <span class="subtitle">them</span>
                <span class="subtitle">directly</span>
                <span class="subtitle">to</span>
                <span class="subtitle">deliver</span>
                <span class="subtitle">an</span>
                <span class="subtitle">important</span>
                <span class="subtitle">message</span>
                <span class="subtitle">about</span>
                <span class="subtitle">that</span>
                <span class="subtitle">criminal</span>
                <span class="subtitle">justice</span>
                <span class="subtitle">professor.</span>
                <span class="subtitle">Here</span>
                <span class="subtitle">goes.</span>
                <span class="subtitle">Fuck</span>
                <span class="subtitle">that</span>
                <span class="subtitle">guy</span>
                <span class="subtitle">and</span>
                <span class="subtitle">he's</span>
                <span class="subtitle">fucking</span>
                <span class="subtitle">YouTube</span>
                <span class="subtitle">videos.</span>
                <span class="subtitle">Stop</span>
                <span class="subtitle">listening</span>
                <span class="subtitle">to</span>
                <span class="subtitle">a</span>
                <span class="subtitle">man</span>
                <span class="subtitle">who</span>
                <span class="subtitle">doesn't</span>
                <span class="subtitle">know</span>
                <span class="subtitle">what</span>
                <span class="subtitle">the</span>
                <span class="subtitle">fuck</span>
                <span class="subtitle">he's</span>
                <span class="subtitle">talking</span>
                <span class="subtitle">about,</span>
                <span class="subtitle">you</span>
                <span class="subtitle">idiot.</span>
            </span>
        </p>
    </div>

</Slide>

<style>

    .content {
        margin: auto;
    }
    
    .sticky {   
        top: 0;
        background-color: #f1f1f14e;
        /* border: 1px black solid; */
        padding: 50px;
        font-size: 3em;
        color: #494949;
    }


    .transcript {
        display: block;
        position: static;
        font-size: 1.5em;
        z-index: -1;
        overflow: hidden;
        text-align: justify;
        color:#6f6f6f
    }

    /* .Joke {
        background-color: #FFADAD;
    } */

    .video-container {
        position: relative;
        width: fit-content;
        height: auto;
        display: inline-block;
        max-width: 100%;
    }

    .scanlines-overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        object-fit: contain;
        z-index: 1;
        opacity: 0.35;
    }

    video {
        width: 100%;
        height: auto;
    }

    video::-webkit-media-controls-panel {
        opacity: 0;
        transition: opacity 0.3s ease;
    }

    video:hover::-webkit-media-controls-panel {
        opacity: 1;
    }

    /* Firefox */
    video {
        --controls-opacity: 0;
    }

    video:hover {
        --controls-opacity: 1;
    }

    .Point {
        background-color: #dbcdf0;
    }

    .Source {
        background-color: #faedcb;
    }

    .Explanation {
        background-color: #f7d9c4;
    }

    @media (min-width: 768px) {
        .content {
            max-width: 100vw; /* Optional: Limit content width for better readability */
            max-height: 100vh; /* Optional: Limit content height for a balanced layout */
            justify-self: center;
            margin:0;
        }

		video {
			max-height: 30vh;
		}

        .sticky {
            font-size: 1.6em;
            top: 30%;
            /* bottom: 30%; */
        }


        .transcript {
            display: block;
            margin: 0;
            position: static;
            z-index: -1;
            overflow: hidden;
            text-align: justify;
            color:#6f6f6f;
            /* background: black; */
			font-size: 1em;
			margin-top: 1em;
        }
    }
</style>