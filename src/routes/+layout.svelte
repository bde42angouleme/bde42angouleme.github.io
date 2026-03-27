<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import Pointer from "../components/Pointer.svelte";

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<Pointer/>
<main>
	{@render children()}
</main>

<style>
</style>