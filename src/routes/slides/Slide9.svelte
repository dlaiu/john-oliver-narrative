<script>
    import { base } from '$app/paths';
	import { browser } from '$app/environment';
	import Slide from '$lib/Slide.svelte';

	import { onMount, onDestroy } from 'svelte';
	let video;
	let captions = [];
	let subtitles = [];
	let durationPerWord = 0.4;
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
							subtitle.style.backgroundColor = '#faedcb';
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
        <p class="sticky">Oliver also shows his supporting <span style="background-color:#faedcb">evidence</span> very clearly.</p>

		<div class="video-container">
			<video bind:this={video} preload="auto" data-autoplay controls muted>
				<source src="{base}/JO_Source_2.mp4" type="video/mp4" />
			</video>
			<img src="{base}/scanlines-fade.png" alt="" class="scanlines-overlay" />
		</div>

        <p class="transcript">
            <span class="caption Point" data-start="00:20:53:16">But lawmakers shouldn't be learning how to perform executions  from one. That legislator then called in this guy, a  high school friend of his and criminal justice professor who put together a presentation  for the legislature in which he tried to prove the method  was painless by, for some reason, playing YouTube videos of kids  passing out from breathing helium.</span>
            <span class="caption Source" data-start="00:00:00:00">
                <span class="subtitle">So</span>
                <span class="subtitle">this</span>
                <span class="subtitle">is</span>
                <span class="subtitle">a</span>
                <span class="subtitle">teenager</span>
                <span class="subtitle">that</span>
                <span class="subtitle">is</span>
                <span class="subtitle">breathing</span>
                <span class="subtitle">helium</span>
                <span class="subtitle">to</span>
                <span class="subtitle">make</span>
                <span class="subtitle">their</span>
                <span class="subtitle">voice</span>
                <span class="subtitle">sound</span>
                <span class="subtitle">funny,</span>
                <span class="subtitle">but</span>
                <span class="subtitle">they're</span>
                <span class="subtitle">not</span>
                <span class="subtitle">really</span>
                <span class="subtitle">thinking</span>
                <span class="subtitle">that</span>
                <span class="subtitle">when</span>
                <span class="subtitle">they're</span>
                <span class="subtitle">breathing</span>
                <span class="subtitle">helium,</span>
                <span class="subtitle">they're</span>
                <span class="subtitle">not</span>
                <span class="subtitle">breathing</span>
                <span class="subtitle">oxygen.</span>
                <span class="subtitle">And</span>
                <span class="subtitle">so</span>
                <span class="subtitle">she's</span>
                <span class="subtitle">trying</span>
                <span class="subtitle">to</span>
                <span class="subtitle">get</span>
                <span class="subtitle">as</span>
                <span class="subtitle">big</span>
                <span class="subtitle">a</span>
                <span class="subtitle">breath</span>
                <span class="subtitle">as</span>
                <span class="subtitle">she</span>
                <span class="subtitle">can,</span>
                <span class="subtitle">and</span>
                <span class="subtitle">in</span>
                <span class="subtitle">a</span>
                <span class="subtitle">second,</span>
                <span class="subtitle">she</span>
                <span class="subtitle">becomes</span>
                <span class="subtitle">hypoxic.</span>
                <span class="subtitle">So</span>
                <span class="subtitle">then</span>
                <span class="subtitle">they</span>
                <span class="subtitle">get</span>
                <span class="subtitle">back</span>
                <span class="subtitle">up</span>
                <span class="subtitle">and</span>
                <span class="subtitle">they're</span>
                <span class="subtitle">giggling</span>
                <span class="subtitle">and</span>
                <span class="subtitle">laughing.</span>
            </span>
            <span class="caption Explanation" data-start="00:21:53:08">Now, obviously,  there's a lot wrong with that. For starters, those kids are voluntarily  depriving themselves of oxygen, not trying to resist, which is what would  likely happen during an execution. So you can't really compare  the two scenarios. But since Oklahoma lawmakers  seem to respond</span>
            <span class="caption Joke" data-start="00:22:04:01">well to videos of people on helium,  allow me to address them directly to deliver an important message  about that criminal justice professor. Here goes. Fuck that guy and he's fucking YouTube  videos. Stop listening to a man who doesn't know what the fuck  he's talking about, you idiot.</span>
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

    .Joke {
        /* background-color: #FFADAD;    */
    }

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