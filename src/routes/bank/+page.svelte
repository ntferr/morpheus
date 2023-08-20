<script>
    import Banklist from "./banklist.svelte";'./baklist.svelte'

    export async function createBank() {
        const bankName = document.getElementById("bankName").value;
        const bankCode = document.getElementById("bankCode").value;

        const res = await fetch('http://127.0.0.1:8000/banks', {
            method: 'POST',
            headers: {
                'Accept':'application/json',
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                "name": bankName,
                "code": bankCode
            })
        })
        
        if(!res.ok) {
            throw new Error(res.json());
        }

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

            <div for="bankCode">
                <label for= "bankCode">Code: <abbr title="required"></abbr></label>
                <br/>
                <input type="text" name="bankCode" id="bankCode"/>
            </div>

            <button on:click={createBank}>Send</button>
        </form>
    </div>
</div>
