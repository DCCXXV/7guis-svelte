<script lang="ts">
    function getTodayString(): string {
        return new Date().toISOString().split('T')[0];
    }

    let option = $state<string>('return flight');
    let goDate: string = $state(getTodayString());
    let returnDate: string = $state(getTodayString());
    let dialog: HTMLDialogElement;

    let disableButton = $derived((option === 'return flight') && (returnDate < goDate));

    function handleSubmit(event: Event) {
        event.preventDefault();
        dialog.showModal();
    }

    function returnFlightDialog(): string {
        if (option === 'return flight') {
            return " to " + returnDate;
        } else {
            return "";
        }
    }
</script>

<svelte:head>
    <title>Flight Booker</title>
</svelte:head>

<section>
    <form id="content">
        <select bind:value={option}>
            <option>one-way flight</option>
            <option>return flight</option>
        </select>
        <input bind:value={goDate} type="date">
        <input bind:value={returnDate} type="date" disabled={option === 'one-way flight'}>
        <button type="submit" onclick="{handleSubmit}" disabled={disableButton}>Book</button>
    </form>
</section>

<dialog bind:this={dialog}>
    <article>
        <header>
            <p>
                <strong>🗓️ Your flight has been booked succesfully! ✈️</strong>
            </p>
        </header>
        <p>
            You have booked a {option} {(option==='return flight') ? "from" : "on"} {goDate}{returnFlightDialog()}.
        </p>
        <p>
            ESC to close
        </p>
    </article>
</dialog>

<style>
    section {
        display: flex;
        min-height: 70vh;
    }

    #content {
        display: grid;
        margin: auto;
        justify-items: center;
        width: 30%;
    }
</style>