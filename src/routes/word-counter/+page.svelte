<script>
    import file from "../../file.json";
    const whatItIs = "Word Counter web tool";
    let content = "";
    let count = "";
    let paragraphStyle = "none";
    function onClick() {
        if (content.trim().length == 0 || content.trim().length == 1) {
            paragraphStyle = "block";
            count = "Please enter more Words, Thankyou!";
            setTimeout(() => {
                count = "";
                paragraphStyle = "none";
            }, 1000);
            return;
        }
        paragraphStyle = "block";
        count = content.split(" ").length.toString() + " words.";
    }
</script>

<svelte:head>
    <title>{whatItIs}</title>
    <meta name="description" content={whatItIs} />
</svelte:head>

<section>
    <h1>{whatItIs}</h1>
    <p style="display:{paragraphStyle}">{count}</p>
    <textarea bind:value={content} required placeholder="Enter your words!" />
    <button on:click={onClick}>Count</button>
    <span><strong>Note: </strong>Tool can count extra space</span>
    <a target="_blank" href={file[0].developer}>Developed by {file[0].name}</a>
    <main>
        Image by <a
            href="https://pixabay.com/users/fabygreen-949897/?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=729173"
            >Faby Green</a
        >
        from
        <a
            href="https://pixabay.com//?utm_source=link-attribution&utm_medium=referral&utm_campaign=image&utm_content=729173"
            >Pixabay</a
        >
    </main>
</section>

<style scoped>
    section {
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        gap: 23px;
        padding: 9px 9px 57px 9px;
        background-image: url("/quotes-729173_640.jpg");
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
        color: white;
    }
    textarea {
        border: none;
        width: 95%;
        height: 770px;
        padding: 6px;
        outline: 0;
        background-color: rgba(223, 223, 223, 0.884);
        color: rgb(59, 59, 59);
        box-shadow:
            rgba(255, 255, 255, 0.4) 5px 5px,
            rgba(255, 255, 255, 0.3) 10px 10px,
            rgba(241, 241, 241, 0.2) 15px 15px,
            rgba(240, 46, 170, 0.1) 20px 20px,
            rgba(218, 218, 218, 0.05) 25px 25px;
    }
    a {
        color: white;
        text-decoration: none;
        position: absolute;
        left: 0px;
        top: 0px;
        opacity: 0.5;
        font-size: 9px;
    }
    button {
        width: 50px;
        height: 50px;
        border-radius: 50%;
    }
    main {
        display: none;
    }
    p {
        padding: 3px;
        background-color: #ffffff;
        color: rgb(59, 59, 59);
    }
    span {
        background-color: #333333b2;
    }
</style>
