<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>

<style>
	main {
		position: relative;
		max-width: 56em;
		background-color: white;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}

	:global(button) {
		background-color: #bb701b;
		padding: 10px 12px 10px 12px;
		color: white;
		font-weight: 500;
		text-transform: uppercase;
		border-radius: 5px;
		font-size: 18px;

	}

	:global(button:hover) {
		background-color: #b66d00;
		cursor: pointer;
	}
</style>

<Nav {segment}/>

<main>
	<slot></slot>
</main>