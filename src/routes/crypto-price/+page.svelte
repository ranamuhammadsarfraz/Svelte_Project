<script>
    import file from "../../file.json";
    import Developer from "../../components/Developer.svelte";
    const pageTitle = "Crypto Price";
    let symbol = "";
    let data = [{ isDisable: false }, { symbol: "" }, { price: "" }];

    const myFunction = () => {
        data[0].isDisable = true;
        fetch("https://api.api-ninjas.com/v1/cryptoprice?symbol=" + symbol, {
            headers: {
                "X-Api-Key": file[0].xyz,
            },
        })
            .then((res) => res.json())
            .then((response) => {
                const { symbol, price, error } = response;
                if (error) {
                    data[1].symbol = error;
                    data[0].isDisable = false;
                    return;
                }

                data[1].symbol = "Symbol: " + symbol;
                data[2].price = "Price: " + price;
                data[0].isDisable = false;
            });
    };
</script>

<svelte:head>
    <title>{pageTitle}</title>
    <meta name="description" content="Tool to show Crypto currency rate." />
</svelte:head>

<div>
    <form method="post" on:submit|preventDefault={myFunction}>
        <h1>{pageTitle}</h1>
        <input
            type="text"
            placeholder="Currency (Example: LTCBTC)"
            required
            bind:value={symbol}
            disabled={data[0].isDisable}
        />
        <button disabled={data[0].isDisable}>convert</button>
        <p>
            {data[1].symbol}
        </p>
        <p>
            {data[2].price}
        </p>
    </form>
    <Developer />
</div>

<style scoped>
    div {
        width: 100%;
        height: 100vh;
        padding: 13px;
        background-color: rgb(0, 0, 0);
        color: silver;
    }
    h1 {
        font-size: 50px;
    }
    form {
        display: grid;
        gap: 6px;
    }
    form input,
    button {
        border-radius: 4px;
        outline: none;
        padding: 4px;
        border: solid 2px white;
        width: 220px;
    }
    form button {
        background-color: green;
        border: none;
        color: white;
    }
    form button:hover {
        background-color: white;
        color: green;
    }
    form button:active {
        opacity: 0.6;
    }
</style>
