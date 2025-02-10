<script lang="ts">
	let props = $props();
</script>

<div
	class="relative h-full overflow-hidden rounded-3xl bg-slate-800 p-px before:pointer-events-none before:absolute before:-top-40 before:-left-40 before:z-10 before:h-80 before:w-80 before:translate-x-[var(--mouse-x)] before:translate-y-[var(--mouse-y)] before:rounded-full before:bg-slate-400 before:opacity-0 before:blur-[100px] before:transition-opacity before:duration-500 before:group-hover:opacity-100 after:pointer-events-none after:absolute after:-top-48 after:-left-48 after:z-30 after:h-96 after:w-96 after:translate-x-[var(--mouse-x)] after:translate-y-[var(--mouse-y)] after:rounded-full after:bg-indigo-500 after:opacity-0 after:blur-[100px] after:transition-opacity after:duration-500 after:hover:opacity-10"
>
	{props}
</div>
