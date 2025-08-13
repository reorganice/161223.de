<script lang="ts">
	import '../app.css';
	import favicon from '$lib/assets/favicon.svg';
	import Header from './Header.svelte';
	import Footer from './Footer.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<div id="app">
	<Header />
	<main>
		{@render children?.()}
	</main>
	<Footer />
</div>

<style>
	#app {
		display: flex;
		flex-direction: column;
		width: 100%;
		overflow: hidden;
	}

	main {
		background-color: rgb(77, 77, 77);
		overflow: hidden;
	}

	:global(a) {
		color: #000000;
		text-decoration: none;
		font-weight: 700;
	}
</style>
