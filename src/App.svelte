<script lang="ts">
	//export let name: string;
	import router from "page";
	import Home from "./pages/Home.svelte";
	import Contact from "./pages/Contact.svelte";
	import About from "./pages/About.svelte";
	import Services from "./pages/Services.svelte";
	let page;

	router("/", () => (page = Home));
	router("/services", () => (page = Services));
	router("/about", () => (page = About));
	router("/contact", () => (page = Contact));

	router.start();

	function pageSwitch(pName: string) {
		window.location.href = `/${pName}`;
	}
</script>

<header>
	<img src="assets/imgs/complogo.png" alt="" class="header-icon" on:click={() => pageSwitch("")}/>
	<div class="header-btns">
		<span on:click={() => pageSwitch("contact")} class="header-btns-contact">Contact</span>
		<span on:click={() => pageSwitch("about")} class="header-btns-about">About Us</span>
		<button class="header-btns-service" on:click={() => pageSwitch("services")}>Services</button>
	</div>
</header>
<svelte:component this={page} />

<style>
	header {
		background-color: rgb(61, 61, 61);
		height: 5em;
	}
	.header-icon {
		margin-left: 1.7em;
		width: 95px;
		height: 80px;
	}
	.header-btns {
		margin-top: 0.7em;
		float: right;
		font-family: "Roboto Condensed", sans-serif;
		margin-right: 6em;
		font-size: 24px;
	}
	.header-btns-service, .header-btns-about, .header-btns-contact{
		padding-right: 1em;
	}
	.header-btns-about:hover, .header-btns-contact:hover {
		color: var(--primary-color);
		transition-duration: 0.5s;
	}
	.header-btns-service {
		display: inline-block;
		padding: 10px;
		font-size: 24px;
		cursor: pointer;
		text-align: center;
		text-decoration: none;
		outline: none;
		color: #fff;
		background-color: var(--primary-color);
		border: none;
		border-radius: 15px;
	}

	.header-btns-service:hover {
		background-color: var(--primary-color);
	}
	.header-btns-service:active {
		background-color: var(--primary-color);
		transition-duration: 0.1s;
		transform: translateY(-5px);
	}
</style>
