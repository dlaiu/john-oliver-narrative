<script>
	import Slide from '$lib/Slide.svelte';

	import { onMount } from 'svelte';
	let video;
	let captions = [];
	let subtitles = [];
	let durationPerWord = 0.28;

	onMount(() => {
		captions = document.querySelectorAll('.caption');

		console.log('Captions:', captions); // Verify captions are selected

		video.addEventListener('timeupdate', () => {
			const currentTime = video.currentTime;
			console.log('Current Time:', currentTime); // Verify video time updates

			captions.forEach((caption) => {
				const start = parseTime(caption.getAttribute('data-start'));
				console.log('Start Time:', start); // Verify start time parsing

				if (currentTime >= start) {
					const subtitles = caption.querySelectorAll('.subtitle');
					console.log('Subtitles:', subtitles); // Verify subtitles are selected

					subtitles.forEach((subtitle, index) => {
						const wordStart = start + index * durationPerWord;

						if (currentTime >= wordStart) {
							subtitle.classList.add('highlighted');
							subtitle.style.backgroundColor = '#f7d9c4';
							console.log(`Adding is-visible to word ${index}`); // Log class addition
						}
					});
				}
			});
		});
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

<Slide bgColor="#8db3cf">
    <div class="content">
        <p class="sticky">He then <span style="background-color:#f7d9c4">elaborates</span> on the relevance of the source, linking it back to his point.</p>

		<video bind:this={video} preload="auto" data-autoplay>
			<source src="/JO_Explanation_2.mp4" type="video/mp4" />
		</video>

        <p class="transcript">
            <span class="caption Point" data-start="00:20:53:16">But lawmakers shouldn't be learning how to perform executions  from one. That legislator then called in this guy, a  high school friend of his and criminal justice professor who put together a presentation  for the legislature in which he tried to prove the method  was painless by, for some reason, playing YouTube videos of kids  passing out from breathing helium.</span>
            <span class="caption Source" data-start="00:21:14:11">So this is a teenager that is breathing helium  to make their voice sound funny, but they're not really thinking that when they're breathing helium,  they're not breathing oxygen. And so she's trying to get as big a breath  as she can, and in a second,  she becomes hypoxic. So then they get back up and they're  giggling and laughing. Now, obviously,  there's a lot wrong with that.</span>
            <span class="caption Explanation" data-start="00:00:00:00">
                <span class="subtitle">Now,</span>
                <span class="subtitle">obviously,</span>
                <span class="subtitle">there's</span>
                <span class="subtitle">a</span>
                <span class="subtitle">lot</span>
                <span class="subtitle">wrong</span>
                <span class="subtitle">with</span>
                <span class="subtitle">that.</span>
                <span class="subtitle">For</span>
                <span class="subtitle">starters,</span>
                <span class="subtitle">those</span>
                <span class="subtitle">kids</span>
                <span class="subtitle">are</span>
                <span class="subtitle">voluntarily</span>
                <span class="subtitle">depriving</span>
                <span class="subtitle">themselves</span>
                <span class="subtitle">of</span>
                <span class="subtitle">oxygen,</span>
                <span class="subtitle">not</span>
                <span class="subtitle">trying</span>
                <span class="subtitle">to</span>
                <span class="subtitle">resist,</span>
                <span class="subtitle">which</span>
                <span class="subtitle">is</span>
                <span class="subtitle">what</span>
                <span class="subtitle">would</span>
                <span class="subtitle">likely</span>
                <span class="subtitle">happen</span>
                <span class="subtitle">during</span>
                <span class="subtitle">an</span>
                <span class="subtitle">execution.</span>
                <span class="subtitle">So</span>
                <span class="subtitle">you</span>
                <span class="subtitle">can't</span>
                <span class="subtitle">really</span>
                <span class="subtitle">compare</span>
                <span class="subtitle">the</span>
                <span class="subtitle">two</span>
                <span class="subtitle">scenarios.</span>
                <span class="subtitle">But</span>
                <span class="subtitle">since</span>
                <span class="subtitle">Oklahoma</span>
                <span class="subtitle">lawmakers</span>
                <span class="subtitle">seem</span>
                <span class="subtitle">to</span>
                <span class="subtitle">respond</span>
            </span>
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
        background-color: #FFADAD;
    }

    video {
        width: 100%;
        height: auto;
    }

    .Point {
        background-color: #dbcdf0;
    }

    .Source {
        background-color: #faedcb;
    }
</style>