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

<main class="text-center p-8">
    <h2 class="text-3xl mb-4">{message}</h2>
    <input
        bind:value={newTodo}
        placeholder="New ToDo"
        class="border p-2 mb-2 w-full"
    />
    <button on:click={createTodo} class="bg-blue-500 text-white px-4 py-2 mr-2">
        Create ToDo
    </button>
    <button on:click={fetchData} class="bg-green-500 text-white px-4 py-2">
        Fetch Data
    </button>

    {#if todos.length > 0}
        <ul class="mt-4">
            {#each todos as { id, content }}
                <li key={id} class="bg-gray-100 p-2 mb-2 rounded">{content}</li>
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
