<script>
    import file from "../../file.json";
    const pageTitle = "Currency Converter (USD)";
    let convertedRate = "";
    let currencyName = "";
    let convertAmount = "";
    let itDisable = false;

    const myFunction = () => {
        itDisable = true;
        convertedRate = "Loading!";
        fetch(
            `https://api.api-ninjas.com/v1/convertcurrency?want=${currencyName.toUpperCase()}&have=USD&amount=${convertAmount}`,
            {
                headers: {
                    "X-Api-Key": file[0].xyz,
                },
            },
        )
            .then((res) => res.json())
            .then((response) => {
                const {
                    new_amount,
                    new_currency,
                    old_currency,
                    old_amount,
                    error,
                } = response;
                if (error) {
                    convertedRate = error;
                    itDisable = false;
                    return;
                }
                convertedRate = `${old_amount} ${old_currency} is ${new_amount} ${new_currency}.`;
                itDisable = false;
            });
    };
</script>

<svelte:head>
    <title>{pageTitle}</title>
    <meta name="description" content="Tool to show USD currency rate." />
</svelte:head>

<div>
    <form method="post" on:submit|preventDefault={myFunction}>
        <h1>{pageTitle}</h1>
        <input
            type="text"
            placeholder="Currency (Example: CNY)"
            required
            bind:value={currencyName}
            disabled={itDisable}
        />
        <input
            type="text"
            placeholder="Amount (Example: 101)"
            required
            bind:value={convertAmount}
            disabled={itDisable}
        />
        <button disabled={itDisable}>convert</button>
        <p>
            {convertedRate}
        </p>
    </form>
    <section>
        Data is controlled by external source. Web Tool is developed by
        <a href={file[0].developer}>{file[0].name}</a>, Thanks.
    </section>
</div>

<style scoped>
    div {
        width: 100%;
        height: 100vh;
        padding: 13px;
        background-color: rgb(22, 22, 34);
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
        width: 200px;
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
    section {
        position: absolute;
        bottom: 0px;
        width: 200px;
        padding: 12px;
    }
    section a {
        text-decoration: none;
        color: #333;
        background-color: #ffffff;
    }
</style>
