<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=f3f4166bd2e2bdc88a9f6f8375f1010a&language=en-US`
		);
		const movieDetail = await res.json();
		if (res.ok) {
			return {
				props: { movieDetail }
			};
		}
	}
</script>

<script>
	export let movieDetail;
</script>

<div class="px-5 my-8 max-w-7xl mx-auto">
	<div class="w-full">
		<img
			class="w-full rounded-2xl"
			src={'https://image.tmdb.org/t/p/original' + movieDetail.backdrop_path}
			alt={movieDetail.title}
		/>
	</div>
	<div>
		<h1 class="pt-4 pb-8 font-bold text-3xl">{movieDetail.title}</h1>
		<p class="py-4 ">{movieDetail.overview}</p>
		<p class="py-4">
			<span class="font-bold">Release date:</span>
			{movieDetail.release_date} <br />
			<span class="font-bold">Budget:</span> ${movieDetail.budget}<br />
			<span class="font-bold">Rating:</span>
			{movieDetail.vote_average}<br />
			<span class="font-bold">Runtime:</span>
			{movieDetail.runtime}mins
		</p>
	</div>
</div>
