<!-- HeartAnimation.svelte -->
<script>
	import { onMount } from 'svelte';
	/**
	 * @type {Element}
	 */
	let heartElement;
	let isVisible = false;

	onMount(() => {
		const observer = new IntersectionObserver(
			([entry]) => {
				isVisible = entry.isIntersecting;
			},
			{
				threshold: 0.1,
				rootMargin: '50px'
			}
		);

		observer.observe(heartElement);

		return () => observer.disconnect();
	});
</script>

<main class="flex flex-col items-center justify-center">
	<div bind:this={heartElement} class="flex items-center justify-center">
		<div
			class="transform transition-all duration-1000 ease-in-out {isVisible
				? 'scale-150 opacity-100'
				: 'scale-50 opacity-0'}"
		>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				width="200"
				height="200"
				viewBox="0 0 24 24"
				fill="#e91e63"
				stroke="#e91e63"
				stroke-width="2"
				stroke-linecap="round"
				stroke-linejoin="round"
				class="transition-transform duration-500 {isVisible ? 'animate-pulse' : ''}"
			>
				<path
					d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"
				/>
			</svg>
		</div>
	</div>

	<div class="mt-8 flex items-center justify-center p-6">
		<p class="text-center text-2xl font-semibold text-pink-600">Love you loads ! ❤️</p>
	</div>
</main>

<style>
	@keyframes pulse {
		0%,
		100% {
			transform: scale(1);
		}
		50% {
			transform: scale(1.05);
		}
	}

	.animate-pulse {
		animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
	}
</style>
