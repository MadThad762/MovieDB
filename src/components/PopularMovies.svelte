<script>
	export let popular;
	import MovieCard from './MovieCard.svelte';
</script>

<div class="max-w-7xl px-5 mx-auto pb-24">
	<h3 class="font-bold text-2xl">Popular Movies</h3>
	<div class="grid gap-5 grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 xl:grid-cols-6">
		{#each popular as movie}
			<MovieCard {movie} />
		{/each}
	</div>
</div>
