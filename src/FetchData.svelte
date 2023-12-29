<!-- src/components/FetchData.svelte -->
<script>
    let message = "";

    async function fetchData() {
        try {
            const response = await fetch("http://localhost:8090/api/hello");
            const data = await response.json();
            message = data.message;
        } catch (error) {
            console.error("Error fetching data:", error);
        }
    }
</script>

<main>
    <h2>{message}</h2>
    <button on:click={fetchData}>Fetch Data</button>
</main>

<style>
    main {
        text-align: center;
        padding: 2em;
    }
</style>
