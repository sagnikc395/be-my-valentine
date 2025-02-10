<script>
	import Footer from '../components/footer.svelte';
	import Header from '../components/header.svelte';
</script>

<div
	class="flex min-h-screen flex-col items-center justify-between bg-neutral-800 p-4 text-neutral-200"
>
	<Header />
	<main class="flex flex-grow items-center justify-center">
		<p class="text-xl">
			this site is inspired by
			<a href="https://mewtru.com/valentine" class="text-pink-500 underline hover:text-pink-300"
				>mewtru's valentine's day
			</a>
		</p>
	</main>
	<Footer />
</div>
