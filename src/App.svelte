<script>
	import FetchData from "./FetchData.svelte";
	import TailwindCss from "./TailwindCSS.svelte";
</script>

<!-- src/App.svelte -->

<TailwindCss />

<main>
	<h1>Hello Svelte</h1>
	<FetchData />
	<!-- 他のコンポーネントや要素も追加できます -->
</main>

<style>
	main {
		text-align: center;
		padding: 2em;
	}
</style>
