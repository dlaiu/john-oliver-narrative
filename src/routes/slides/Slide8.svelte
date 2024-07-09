<script>
	import Slide from '$lib/Slide.svelte';

	import { onMount } from 'svelte';
	let video;
	let captions = [];
	let subtitles = [];
	let durationPerWord = 0.32;

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
							subtitle.style.backgroundColor = '#dbcdf0';
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
		<p class="sticky">
			Much like the essays we were taught to write in middle school, Oliver explicitly states the
			<span style="background-color:#dbcdf0">point</span> he is trying to make.
		</p>

		<video bind:this={video} preload="auto" data-autoplay>
			<source src="/JO_Point_2.mp4" type="video/mp4" />
		</video>

		<p class="transcript">
			<span class="caption Point" data-start="00:00:00:00">
				<span class="subtitle">But</span> <span class="subtitle">lawmakers</span>
				<span class="subtitle">shouldn't</span> <span class="subtitle">be</span>
				<span class="subtitle">learning</span> <span class="subtitle">how</span>
				<span class="subtitle">to</span> <span class="subtitle">perform</span>
				<span class="subtitle">executions</span> <span class="subtitle">from</span>
				<span class="subtitle">one.</span> <span class="subtitle">That</span>
				<span class="subtitle">legislator</span> <span class="subtitle">then</span>
				<span class="subtitle">called</span> <span class="subtitle">in</span>
				<span class="subtitle">this</span> <span class="subtitle">guy,</span>
				<span class="subtitle">a</span> <span class="subtitle">high</span>
				<span class="subtitle">school</span> <span class="subtitle">friend</span>
				<span class="subtitle">of</span> <span class="subtitle">his</span>
				<span class="subtitle">and</span> <span class="subtitle">criminal</span>
				<span class="subtitle">justice</span> <span class="subtitle">professor</span>
				<span class="subtitle">who</span> <span class="subtitle">put</span>
				<span class="subtitle">together</span> <span class="subtitle">a</span>
				<span class="subtitle">presentation</span> <span class="subtitle">for</span>
				<span class="subtitle">the</span> <span class="subtitle">legislature</span>
				<span class="subtitle">in</span> <span class="subtitle">which</span>
				<span class="subtitle">he</span> <span class="subtitle">tried</span>
				<span class="subtitle">to</span> <span class="subtitle">prove</span>
				<span class="subtitle">the</span> <span class="subtitle">method</span>
				<span class="subtitle">was</span> <span class="subtitle">painless</span>
				<span class="subtitle">by,</span> <span class="subtitle">for</span>
				<span class="subtitle">some</span> <span class="subtitle">reason,</span>
				<span class="subtitle">playing</span> <span class="subtitle">YouTube</span>
				<span class="subtitle">videos</span> <span class="subtitle">of</span>
				<span class="subtitle">kids</span> <span class="subtitle">passing</span>
				<span class="subtitle">out</span> <span class="subtitle">from</span>
				<span class="subtitle">breathing</span> <span class="subtitle">helium</span>
			</span>
			<span class="caption Source" data-start="00:21:14:11"
				>So this is a teenager that is breathing helium to make their voice sound funny, but they're
				not really thinking that when they're breathing helium, they're not breathing oxygen. And so
				she's trying to get as big a breath as she can, and in a second, she becomes hypoxic. So
				then they get back up and they're giggling and laughing. Now, obviously, there's a lot wrong
				with that.</span
			>
			<span class="caption Explanation" data-start="00:21:53:08"
				>For starters, those kids are voluntarily depriving themselves of oxygen, not trying to
				resist, which is what would likely happen during an execution. So you can't really compare
				the two scenarios. But since Oklahoma lawmakers seem to respond</span
			>
			<span class="caption Joke" data-start="00:22:04:01"
				>well to videos of people on helium, allow me to address them directly to deliver an
				important message about that criminal justice professor. Here goes. Fuck that guy and he's
				fucking YouTube videos. Stop listening to a man who doesn't know what the fuck he's talking
				about, you idiot.</span
			>
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
		padding: 50px;
		font-size: 3em;
		color: #494949;
	}

	.highlighted {
		background-color: red !important;
		/* Adding !important to ensure it overrides any other styles */
		/* transition: background-color 0.5s ease; */
	}

	.transcript {
		display: block;
		position: static;
		font-size: 1.5em;
		z-index: -1;
		overflow: hidden;
		text-align: justify;
		color: #6f6f6f;
	}

	.Joke {
		background-color: #ffadad;
	}

	video {
		width: 100%;
		height: auto;
	}
</style>
