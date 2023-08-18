<script>
    import Banklist from "./banklist.svelte";'./baklist.svelte'

    export async function createBank() {
        const bankName = document.getElementById("bankName").value;
        const bankNumber = document.getElementById("bankNumber").value;

        const res = await fetch('http://127.0.0.1:8000/banks', {
            method: 'POST',
            headers: {
                'Accept':'application/json',
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                "name": bankName,
                "number": bankNumber
            })
        })
        location.reload(true)
    }
</script>

<div class=header>
    <h1>Morpheus</h1>
</div>    
<div>
<div class=content>
        <a href="/..">&#129184;</a>
        <h2>Bancos</h2>
        <Banklist/>
        <form>
            <div for="bankName">
                <label for= "bankName">Name: <abbr title="required"></abbr></label>
                <br/>
                <input type="text" name="bankName" id="bankName"/>
            </div>

            <div for="bankNumber">
                <label for= "bankNumber">Number: <abbr title="required"></abbr></label>
                <br/>
                <input type="text" name="bankNumber" id="bankNumber"/>
            </div>

            <button on:click={createBank}>Send</button>
        </form>
    </div>
</div>
