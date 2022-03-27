<script context="module">
	export async function load({ fetch }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/popular?api_key=${
				import.meta.env.VITE_API_KEY
			}&language=en-US&page=1`
		);
		const data = await res.json();
		if (res.ok) {
			return {
				props: { popular: data.results }
			};
		}
	}
</script>

<script>
	import PopularMovies from '../components/PopularMovies.svelte';
	import { fly } from 'svelte/transition';
	export let popular;
</script>

<section in:fly={{ duration: 400, delay: 400 }} out:fly={{ duration: 400 }}>
	<PopularMovies {popular} />
</section>

<style>
</style>
