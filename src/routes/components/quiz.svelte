<!-- Quiz.svelte -->
<script>
	import { tweened } from 'svelte/motion';
	import { fade } from 'svelte/transition';
	import { cubicOut } from 'svelte/easing';

	export let onAccept = () => {};
	let noCount = 0;

	const yesScale = tweened(1, {
		duration: 300,
		easing: cubicOut
	});

	const noScale = tweened(1, {
		duration: 300,
		easing: cubicOut
	});

	const noMessages = [
		'Are you sure? 🥺',
		'Really sure? 😢',
		'Think again! 💭',
		'Last chance! 💝',
		'Pretty please! 🙏'
	];

	function handleNo() {
		noCount = (noCount + 1) % (noMessages.length + 1);

		if (noCount === 0) {
			yesScale.set(1);
			noScale.set(1);
		} else {
			yesScale.set(1 + noCount * 0.2);
			noScale.set(Math.max(0.5, 1 - noCount * 0.1));
		}
	}

	$: message = noCount > 0 ? noMessages[Math.min(noCount - 1, noMessages.length - 1)] : '';
</script>

<div class="flex min-h-[50vh] flex-col items-center justify-center gap-8" transition:fade>
	<h1 class="text-4xl font-bold text-pink-600">Will you be my Valentine?</h1>

	<div class="flex min-w-[400px] items-center justify-center gap-8">
		<div style="transform: scale({$yesScale})" class="transform transition-all duration-300">
			<button
				on:click={onAccept}
				class="rounded-lg bg-pink-600 px-8 py-4 text-xl font-bold whitespace-nowrap text-white transition-all hover:bg-pink-700"
			>
				Yes
			</button>
		</div>

		<div style="transform: scale({$noScale})" class="transform transition-all duration-300">
			<button
				on:click={handleNo}
				class="rounded-lg bg-neutral-600 px-8 py-4 text-xl font-bold whitespace-nowrap text-white transition-all hover:bg-neutral-700"
			>
				No
			</button>
		</div>
	</div>

	{#if message}
		<p class="text-lg text-pink-500" transition:fade>{message}</p>
	{/if}
</div>

<style>
	div {
		transform-origin: center;
	}
</style>
