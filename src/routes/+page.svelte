<script>
	import Footer from './components/footer.svelte';
	import Header from './components/header.svelte';
	import Heart from './components/heart.svelte';
	import Quiz from './components/quiz.svelte';

	let accepted = false;
</script>

<div
	class="flex min-h-screen flex-col items-center justify-between bg-neutral-800 p-4 text-neutral-200"
>
	<Header />
	<main class="flex flex-grow items-center justify-center">
		{#if accepted}
			<div class="relative flex flex-col items-center gap-4">
				<img src="/pikachu.gif" alt="happy pikachy :D" class="h-64 w-64 object-contain p-4" />
				<Heart />
			</div>
		{:else}
			<Quiz onAccept={() => (accepted = true)} />
		{/if}
	</main>
	<Footer />
</div>
