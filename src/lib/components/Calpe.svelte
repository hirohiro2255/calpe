<script lang="ts">
	import Lexer from '$lib/utils/lexer';
	import { Parser, Calculator } from '$lib/utils/calculator';
	let isFocused = false;
	let state = '';

	function onFocus() {
		isFocused = true;
	}
	function closeCalc() {
		isFocused = false;
	}

	function handleResult() {
		const lexer = new Lexer(state);
		const parser = new Parser(lexer);
		const calc = new Calculator(parser);
		state = calc.cc().toString();
	}
</script>

<input class="calpe-input" type="number" readonly={isFocused} on:focus={(event) => onFocus()} />
{#if isFocused}
	<section class="calpe-container">
		<div class="screen-container">
			<p class="screen-result">{state.length === 0 ? '0' : state}</p>
		</div>
		<div class="keypad-container">
			<div class="keypad-wrapper">
				<button on:click={() => (state = state + '7')}>7</button>
				<button on:click={() => (state = state + '8')}>8</button>
				<button on:click={() => (state = state + '9')}>9</button>
				<button
					on:click={() => (state = state.length === 0 ? '' : state.slice(0, state.length - 1))}
					>C</button
				>
				<button on:click={() => (state = state + '4')}>4</button>
				<button on:click={() => (state = state + '5')}>5</button>
				<button on:click={() => (state = state + '6')}>6</button>
				<button on:click={() => (state = state.length === 0 ? '' : state + '+')}>+</button>
				<button on:click={() => (state = state + '1')}>1</button>
				<button on:click={() => (state = state + '2')}>2</button>
				<button on:click={() => (state = state + '3')}>3</button>
				<button>-</button>
				<button>.</button>
				<button on:click={() => (state = state + '0')}>0</button>
				<button>/</button>
				<button>x</button>
				<button>AC</button>
				<button on:click={handleResult}>=</button>
			</div>
			<button class="close-button" on:click={closeCalc}>Close</button>
		</div>
	</section>
{/if}

<style>
	* {
		box-sizing: border-box;
	}

	:global(html),
	:global(body) {
		margin: 0;
		padding: 0;
	}
	.calpe-container {
		width: 100%;
		max-width: 300px;
		margin-right: auto;
		margin-left: auto;
	}

	.screen-result {
		text-align: right;
	}

	.keypad-wrapper {
		display: grid;
		grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
		grid-template-columns: 1fr 1fr 1fr 1fr;
		gap: 3px;
	}
</style>
