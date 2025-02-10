<!-- Quiz.svelte -->
<script>
	import { spring } from 'svelte/motion';
	import { fade } from 'svelte/transition';

	export let onAccept = () => {};
	let noCount = 0;
	let yesScale = spring(1);
	let noScale = spring(1);

	function handleNo() {
		noCount++;
		yesScale.set(1 + noCount * 0.2); // Increase yes button size by 20% each time
		noScale.set(Math.max(0.5, 1 - noCount * 0.1)); // Decrease no button size, but not smaller than 50%
	}
</script>

<div class="flex min-h-[50vh] flex-col items-center justify-center gap-8" transition:fade>
	<h1 class="text-4xl font-bold text-pink-600">Will you be my Valentine?</h1>

	<div class="flex gap-4">
		<button
			style="transform: scale({$yesScale})"
			on:click={onAccept}
			class="transform rounded-lg bg-pink-600 px-8 py-4 text-xl font-bold text-white transition-all hover:bg-pink-700"
		>
			Yes
		</button>

		<button
			style="transform: scale({$noScale})"
			on:click={handleNo}
			class="transform rounded-lg bg-neutral-600 px-8 py-4 text-xl font-bold text-white transition-all hover:bg-neutral-700"
		>
			No
		</button>
	</div>

	{#if noCount > 0}
		<p class="text-lg text-pink-500">Are you sure? 🥺</p>
	{/if}
</div>
