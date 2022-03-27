<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/search/movie?api_key=${
				import.meta.env.VITE_API_KEY
			}&language=en-US&query=${params.id}&page=1&include_adult=false`
		);
		const data = await res.json();
		if (res.ok) {
			return {
				props: { searchedMovie: data.results }
			};
		}
	}
</script>

<script>
	import MovieCard from '../../components/MovieCard.svelte';
	import { fly } from 'svelte/transition';
	export let searchedMovie;
</script>

<div
	class="max-w-7xl px-5 mx-auto"
	in:fly={{ duration: 400, delay: 400 }}
	out:fly={{ duration: 400 }}
>
	<h3 class="font-bold text-2xl">Search Results</h3>
	<div class="grid gap-5 grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 xl:grid-cols-6">
		{#each searchedMovie as movie}
			<MovieCard {movie} />
		{/each}
	</div>
</div>
