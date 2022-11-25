<script>
	import Counters from './Counters.svelte';
</script>

<svelte:head>
	<title>EZ Counter</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<Counters />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
