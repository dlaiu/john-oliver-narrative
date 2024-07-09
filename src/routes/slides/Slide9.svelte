<script>
    import { base } from '$app/paths';
	import Slide from '$lib/Slide.svelte';

	import { onMount } from 'svelte';
	let video;
	let captions = [];
	let subtitles = [];
	let durationPerWord = 0.4;

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
							subtitle.style.backgroundColor = '#faedcb';
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
        <p class="sticky">Oliver also shows his supporting <span style="background-color:#faedcb">evidence</span> very clearly.</p>

		<video bind:this={video} preload="auto" data-autoplay>
			<source src="{base}/JO_Source_2.mp4" type="video/mp4" />
		</video>

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
        background-color: #FFADAD;
    }

    video {
        width: 100%;
        height: auto;
    }

    .Point {
        background-color: #dbcdf0;
    }
</style>