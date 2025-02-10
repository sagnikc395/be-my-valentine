<script>
	import Footer from './components/footer.svelte';
	import Header from './components/header.svelte';
	import Heart from './components/heart.svelte';
	import Quiz from './components/quiz.svelte';
	import { fade, scale } from 'svelte/transition';
	import { quartOut } from 'svelte/easing';

	let accepted = false;
</script>

<div
	class="flex min-h-screen flex-col items-center justify-between bg-neutral-800 p-4 text-neutral-200"
>
	<Header />
	<main class="flex flex-grow items-center justify-center">
		{#if accepted}
			<div
				class="relative flex flex-col items-center gap-12 p-8"
				in:scale={{
					duration: 700,
					delay: 300,
					opacity: 0,
					start: 0.95,
					easing: quartOut
				}}
			>
				<img
					src="/pikachu.gif"
					alt="Happy Pikachu"
					class="h-64 w-64 object-contain p-4"
					in:scale={{
						duration: 700,
						delay: 600,
						opacity: 0,
						start: 0.8,
						easing: quartOut
					}}
				/>
				<div
					in:scale={{
						duration: 700,
						delay: 800,
						opacity: 0,
						start: 0.8,
						easing: quartOut
					}}
				>
					<Heart />
				</div>
			</div>
		{:else}
			<div in:fade={{ duration: 300 }} out:fade={{ duration: 200 }}>
				<Quiz onAccept={() => (accepted = true)} />
			</div>
		{/if}
	</main>
	<Footer />
</div>
