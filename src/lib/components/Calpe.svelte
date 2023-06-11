<script lang="ts">
	let isFocused = false;

	function onFocus() {
		isFocused = true;
	}
	function outOfFocus() {
		isFocused = false;
	}
</script>

<input class="calpe-input" type="number" readonly={isFocused} on:focus={(event) => onFocus()} />
{#if isFocused}
	<section class="calpe-container">
		<div class="screen-container">
			<p class="screen-result">0</p>
		</div>
		<div class="keypad-container">
			<div class="keypad-wrapper">
				<button>7</button>
				<button>8</button>
				<button>9</button>
				<button>C</button>
				<button>4</button>
				<button>5</button>
				<button>6</button>
				<button>+</button>
				<button>1</button>
				<button>2</button>
				<button>3</button>
				<button>-</button>
				<button>.</button>
				<button>0</button>
				<button>/</button>
				<button>x</button>
				<button>AC</button>
				<button>=</button>
			</div>
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
	}
</style>
