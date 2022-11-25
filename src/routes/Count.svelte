<script>
	import { createEventDispatcher } from 'svelte';
	const dispatcher = createEventDispatcher();

	export let label = 'Count';
	export let count = 0;
	export let color = 'red';
	export let id = '';


	function increment() {
		dispatcher('counterUpdate', { id, count: count + 1 });
	}

	function decrement() {
		if (count === 0) return;
		dispatcher('counterUpdate', { id, count: count - 1 });
	}
</script>

<div class="counter counter--{color}">
	<button class="button" on:click={decrement}>-</button>
	<div class="count">
		<span
			class="counter__label"
			contenteditable={true}
			on:input={(e) => dispatcher('counterUpdate', { id, label: e.target.innerText })}>{label}</span
		>: {count}
	</div>
	<button class="button" on:click={increment}>+</button>
</div>

<style>
	:root {
		--orange: 25;
		--mint: 165;
		--red: 6;
		--green: 107;
		--purple: 250;

		--color-medium-orange: hsl(var(--orange), 90%, 50%);
		--color-light-orange: hsl(var(--orange), 90%, 80%);
		--color-dark-orange: hsl(var(--orange), 90%, 20%);
		--color-white-orange: hsl(var(--orange), 90%, 80%);

		--color-medium-blue: hsl(var(--mint), 90%, 50%);
		--color-light-blue: hsl(var(--mint), 90%, 80%);
		--color-dark-blue: hsl(var(--mint), 90%, 20%);
		--color-white-blue: hsl(var(--mint), 90%, 80%);
		--color-black-blue: hsl(var(--mint), 95%, 20%);

		--color-medium-red: hsl(var(--red), 90%, 50%);
		--color-light-red: hsl(var(--red), 90%, 80%);
		--color-dark-red: hsl(var(--red), 90%, 20%);
		--color-white-red: hsl(var(--red), 90%, 80%);
		--color-black-red: hsl(var(--red), 95%, 20%);

		--color-medium-green: hsl(var(--green), 90%, 50%);
		--color-light-green: hsl(var(--green), 90%, 80%);
		--color-dark-green: hsl(var(--green), 90%, 20%);
		--color-white-green: hsl(var(--green), 90%, 80%);
		--color-black-green: hsl(var(--green), 95%, 20%);

		--color-medium-purple: hsl(var(--purple), 90%, 50%);
		--color-light-purple: hsl(var(--purple), 90%, 80%);
		--color-dark-purple: hsl(var(--purple), 90%, 20%);
		--color-white-purple: hsl(var(--purple), 90%, 80%);
		--color-black-purple: hsl(var(--purple), 95%, 20%);

		--color-medium: ;
		--color-light: ;
		--color-dark: ;
		--color-white: ;

		--soft-corner: 0.4rem;

		--btn-square: 3.2rem;
	}
	.counter {
		padding: 0.4rem;
		background-color: var(--color-light);
		width: 100%;
		display: flex;
		align-items: center;
		justify-content: space-between;
		color: var(--color-dark);
	}

	/* NOTE: there's a better way to declare rules for each color.
   */
	.counter--red {
		--color-medium: var(--color-medium-red);
		--color-light: var(--color-light-red);
		--color-dark: var(--color-dark-red);
		--color-white: var(--color-white-red);
	}

	.counter--mint {
		--color-medium: var(--color-medium-mint);
		--color-light: var(--color-light-mint);
		--color-dark: var(--color-dark-mint);
		--color-white: var(--color-white-mint);
	}
	.counter--blue {
		--color-medium: var(--color-medium-blue);
		--color-light: var(--color-light-blue);
		--color-dark: var(--color-dark-blue);
		--color-white: var(--color-white-blue);
	}
	.counter--orange {
		--color-medium: var(--color-medium-orange);
		--color-light: var(--color-light-orange);
		--color-dark: var(--color-dark-orange);
		--color-white: var(--color-white-orange);
	}
	.counter--green {
		--color-medium: var(--color-medium-green);
		--color-light: var(--color-light-green);
		--color-dark: var(--color-dark-green);
		--color-white: var(--color-white-green);
	}

	.counter--purple {
		--color-medium: var(--color-medium-purple);
		--color-light: var(--color-light-purple);
		--color-dark: var(--color-dark-purple);
		--color-white: var(--color-white-purple);
	}

	.counter label {
		margin-right: 10px;
	}

	.counter .button {
		flex: none;
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 1.8rem;
		cursor: pointer;
		width: var(--btn-square);
		height: var(--btn-square);
		color: var(--color-dark);
		border-radius: var(--soft-corner);
		border: 1px solid var(--color-medium);
		background-color: var(--color-medium);
	}

	.counter .count {
		flex: 1;
		font-size: 24px;
		margin: 0 10px;
		text-align: center;
	}
</style>
