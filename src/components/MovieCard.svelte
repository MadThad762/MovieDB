<script>
	export let movie;
</script>

<div class="mx-auto">
	<a sveltekit:prefetch sveltekit:noscroll href={'/movie/' + movie.id}>
		<img
			class="rounded-lg mt-5 mb-3"
			src={'https://image.tmdb.org/t/p/w500' + movie.poster_path}
			alt={movie.title}
		/>
	</a>
	<div class="">
		<h2 class="font-semibold text-lg">{movie.title}</h2>
		<p class="text-sm">{movie.release_date}</p>
	</div>
</div>
