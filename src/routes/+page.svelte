<script>
	import Developer from "../components/Developer.svelte";
	const what = "Web Tools";
	import Counter from "./Counter.svelte";
	import welcome from "$lib/images/svelte-welcome.webp";
	import welcome_fallback from "$lib/images/svelte-welcome.png";
	const myArr = [
		{
			href: "/currency-converter",
			title: "Currency Converter",
		},
		{
			href: "/crypto-price",
			title: "Crypto Price Checker",
		},
		{
			href: "/word-counter",
			title: "Word Counter web tool",
		},
	];
</script>

<svelte:head>
	<title>{what}</title>
	<meta name="description" content={what} />
</svelte:head>

<section>
	<h1>{what}</h1>
	<ul>
		{#each myArr as name, index}
			<li><a href={name.href}>{index} - {name.title}</a></li>
		{/each}
	</ul>
	<Developer />
</section>

<style>
	section {
		width: 100%;
		height: 100vh;
		background-color: #333;
		text-align: center;
		display: flex;
		flex-direction: column;
		padding: 12px;
		gap: 9px;
	}
	section a {
		color: silver;
	}
</style>
