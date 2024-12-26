<script>
	import '@fontsource/hepta-slab';
</script>

<svelte:head>
	<title>generico</title>
	<meta name="description" content="nomeGenerico" />
</svelte:head>

<slot />

<style>
	:global(body) {
		font-family: 'Hepta Slab', serif;
		margin: 0;
		padding: 0;
	}
</style>
