<script>
	import 'reveal.js/dist/reveal.css';
	import { base } from '$app/paths';

	import Reveal from 'reveal.js';
	import { onMount, tick } from 'svelte';
	import Presentation from './Presentation.svelte';

	export let app;
	export let reveal;

	onMount(async () => {
		await tick();
		const deck = new Reveal(reveal);
		deck.initialize();
	});
</script>

<svelte:head>
	<!-- <title>{app.name}</title> -->
</svelte:head>

<!-- Top overlay layer covering everything -->
<div class="top-overlay-layer" style="--grain-url: url({base}/grain.jpg);"></div>

<div class="reveal">
	<div class="slides">
		<Presentation />
	</div>
</div>

<style>
	div {
		font-family: Georgia, 'Times New Roman', Times, serif;
	}

	.top-overlay-layer {
		position: fixed;
		top: 0;
		left: 0;
		width: 100vw;
		height: 100vh;
		background-color: rgba(0, 0, 0, 0.05);
		background-image: var(--grain-url);
		background-size: cover;
		background-position: center;
		background-repeat: repeat;
		pointer-events: none;
		z-index: 9999;
		opacity: 0.05;
	}
</style>
