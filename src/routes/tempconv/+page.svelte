<script lang="ts">
    let celsius: number = $state(0)
    let fahrenheit: number = $state(0)

    function calcFahrenheit() {
        fahrenheit = Math.round((celsius * (9/5) + 32) * 100) / 100
    }

    function calcCelsius() {
        celsius = Math.round(((fahrenheit - 32) * (5 / 9)) * 100) / 100
    }

</script>

<svelte:head>
    <title>Temperature Converter</title>
</svelte:head>

<section>
    <div id="content">
        <div>
            <label for="celsius">Celsius</label>
            <input type="number" name="celsius" onchange="{calcFahrenheit}" bind:value={celsius}/>
        </div>
        <div>
            <label for="fahrenheit">Fahrenheit</label>
            <input type="number" onchange="{calcCelsius}" name="fahrenheit" bind:value={fahrenheit} />
        </div>
    </div>
</section>

<style>
    section {
        display: flex;
        height: 70vh;
    }

    input {
        text-align: right;
    }

    #content {
        display: grid;
        margin: auto;
        justify-items: center;
    }
</style>