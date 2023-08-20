<script>
        import {onMount} from 'svelte'

        let listOfBanks = [];


        onMount(async () => {
            const res = await fetch('http://127.0.0.1:8000/banks/all', {
                method: 'GET',
                headers: {
                    'Accept': 'application/json',
                    'Content-Type': 'application/json',
                },
            });
            listOfBanks = await res.json();
        });
</script>

<div class="listOfBanks">
    <ul>
        <ul><p>Name - Code</p></ul>
        {#each listOfBanks as object}
            <ul>{object.name} - {object.code}</ul>
        {/each}
    </ul>
</div>