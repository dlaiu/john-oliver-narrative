<script>
	import Slide from '$lib/Slide.svelte';

	import { onMount } from 'svelte';
	let video;
	let captions = [];
	let subtitles = [];
	let durationPerWord = 0.35;

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
							subtitle.style.backgroundColor = '#FFADAD';
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
        <p class="sticky">He then uses the <span style="background-color:#FFADAD">joke</span> to puncutate the point he's trying to make.</p>

		<video bind:this={video} preload="auto" data-autoplay>
			<source src="/JO_Joke_Landscape.mp4" type="video/mp4" />
		</video>

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

    .Explanation {
        background-color: #f7d9c4;
    }
</style>