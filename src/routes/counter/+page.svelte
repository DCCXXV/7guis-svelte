<script lang="ts">
    let count: number = $state(0);

    function increment() {
        count++;
    }
</script>

<svelte:head>
    <title>Counter</title>
</svelte:head>

<section>
    <div id="content">
        <span id="number">{count}</span>
        <button onclick={increment}>Count</button>
    </div>
</section>

<style>
    section {
        display: flex;
        min-height: 70vh;
    }

    #content {
        display: grid;
        margin: auto;
        justify-items: center;
    }
    #number {
        font-size: 5rem;
        font-weight: bold;
    }
</style>