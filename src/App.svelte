<script>
	export let name;
</script>

<main>
	<h1>Hello {name}!</h1>
	<h2>TODO APP</h2>

	<!-- App.svelte -->
	<!-- App.svelte -->
	<script>
		import TodoList from "./TodoList.svelte";
	</script>

	<TodoList />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	h2 {
		color: pink;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 50;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
