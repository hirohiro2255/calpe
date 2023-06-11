<script lang="ts">
	import '$lib/assets/sanitize.css';
	import calc from '$lib/assets/calculator.svg';
	let isFocused = false;

	function onFocus() {
		isFocused = true;
	}
	function outOfFocus() {
		isFocused = false;
	}
</script>

<input
	class="calpe-input"
	type="number"
	readonly={isFocused}
	on:focus={(event) => onFocus()}
	on:blur={(event) => outOfFocus()}
/>
{#if isFocused}
	<section class="calculator-container">
		<h1>Calculator</h1>
	</section>
{/if}

<style>
	.calpe-input {
		text-align: right;
		background-image: url(./../assets/calculator.svg);
		background-repeat: no-repeat;
	}
</style>
