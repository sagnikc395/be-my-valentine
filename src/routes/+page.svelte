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
			<Heart />
		{:else}
			<Quiz onAccept={() => (accepted = true)} />
		{/if}
	</main>
	<Footer />
</div>
