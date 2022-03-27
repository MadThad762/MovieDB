<script>
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';

	let inputValue = '';
	let active = false;

	function cancelInactive() {
		if (inputValue) {
			active = true;
		} else {
			active = false;
		}
	}
	function submitSearch() {
		goto('/search/' + inputValue);
	}
</script>

<div class="max-w-7xl mx-auto px-1">
	<form on:submit|preventDefault={submitSearch} class="relative w-80 m-4">
		{#if !active}
			<label
				in:fly={{ y: -10, duration: 500 }}
				out:fly={{ y: -10, duration: 500 }}
				class="font-medium absolute text-md top-1/2 left-0 -translate-y-2/4 pointer-events-none text-white px-4"
				for="search_movie">Search Movies</label
			>
		{/if}
		<input
			on:blur={cancelInactive}
			on:focus={() => (active = true)}
			bind:value={inputValue}
			class={active
				? 'w-full py-2 px-4 border-0 outline-none text-white font-semibold bg-neutral-700 rounded-md'
				: 'w-full py-2 px-4 border-0 outline-none text-white font-semibold bg-neutral-600 rounded-md'}
			name="search_movie"
			type="text"
		/>
		{#if inputValue}
			<button
				in:fly={{ x: 0, duration: 500 }}
				out:fly={{ x: 0, duration: 500 }}
				class="px-4 bg-neutral-800 text-white font-semibold border-none absolute bottom-1/2 right-0 translate-y-2/4 h-full rounded-tr-lg rounded-br-lg cursor-pointer "
				>Search</button
			>
		{/if}
	</form>
</div>
