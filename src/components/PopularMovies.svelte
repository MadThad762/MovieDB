<script>
	export let popular;
	import MovieCard from './MovieCard.svelte';
</script>

<h3 class="py-0 px-5 xl:px-12 2xl:px-32">Popular Movies</h3>
<div
	class="grid gap-5 grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 xl:grid-cols-6 2xl:grid-cols-7 px-5 xl:px-12 2xl:px-32"
>
	{#each popular as movie}
		<MovieCard {movie} />
	{/each}
</div>
