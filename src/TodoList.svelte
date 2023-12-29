<!-- TodoList.svelte -->
<script>
    import { onMount } from "svelte";

    export let todoList = [];

    // バックエンドからデータを取得する処理
    onMount(async () => {
        const response = await fetch("http://localhost:8080/todos"); // バックエンドのAPIエンドポイント
        const data = await response.json();
        todoList = data;
    });
</script>

{#each todoList as todo (todo.id)}
    <TodoItem {todo} />
{/each}
