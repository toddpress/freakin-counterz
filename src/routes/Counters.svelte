<script>
	import { onMount } from 'svelte';
	import Count from './Count.svelte';

	let colors = ['orange', 'red', 'blue', 'green', 'purple'];

	let counters = [];

	function addCounter() {
		const newCounter = {
			id: `counter-${counters.length + 1}`,
			label: `Counter`,
			count: 0,
			color: getRandomColor()
		};

		counters = [...counters, newCounter];
	}

	function updateCounter(ev) {
		const { id, ...props } = ev.detail;
		const idx = counters.findIndex((c) => c.id === id);
		counters[idx] = {
			...counters[idx],
			...props
		};
	}

	function getRandomColor() {
		const color = colors[Math.floor(Math.random() * colors.length)];
		return color;
	}

	onMount(() => {
		addCounter(); // Add an initial counter when the component mounts
	});
</script>

<div class="counter-list">
	{#each counters as counter, i}
		<Count
			id={counter.id}
			color={counter.color}
			label={counter.label}
			count={counter.count}
			on:counterUpdate={updateCounter}
		/>
	{/each}

	<button class="add-button" on:click={addCounter}>Add Counter</button>

	<pre>
  {JSON.stringify(counters, null, 4)}
  </pre>
</div>

<style>
	.counter-list {
		display: flex;
		flex-direction: column;
		gap: 10px;
	}

	.add-button {
		cursor: pointer;
		font-size: 1.2rem;
		padding: 10px;
		background-color: #4caf50;
		color: white;
		border: none;
		border-radius: 4px;
	}
</style>
