<!-- src/components/FetchData.svelte -->
<script>
    let message = "";
    let newTodo = "";
    let todos = [];

    async function fetchData() {
        try {
            const response = await fetch("http://localhost:8090/api/todos");
            todos = await response.json();
        } catch (error) {
            console.error("Error fetching data:", error);
        }
    }

    async function createTodo() {
        try {
            const response = await fetch("http://localhost:8090/api/todos", {
                method: "POST",
                headers: {
                    "Content-Type": "application/json",
                },
                body: JSON.stringify({ content: newTodo }),
            });
            const data = await response.json();
            console.log("Created Todo:", data);
            fetchData(); // ToDoが作成されたら再度データを取得
        } catch (error) {
            console.error("Error creating Todo:", error);
        }
    }
</script>

<main>
    <h2>{message}</h2>
    <input bind:value={newTodo} placeholder="New ToDo" />
    <button on:click={createTodo}>Create ToDo</button>
    <button on:click={fetchData}>Fetch Data</button>

    {#if todos.length > 0}
        <ul>
            {#each todos as { id, content }}
                <li key={id}>{content}</li>
            {/each}
        </ul>
    {/if}
</main>

<style>
    main {
        text-align: center;
        padding: 2em;
    }
</style>
