<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
	import Tabs from './shared/Tabs.svelte';

	let items = ["Current Polls", "Add new poll"];
	let activeItem = "Current Polls";

	function tabChange(e) {
		activeItem = e.detail;
	}
</script>

<main>
	<Header/>
	<Tabs {activeItem} {items} on:tabChange = {tabChange}/>
		{#if activeItem === "Current Polls"}
			<p>Current Polls Page goes here</p>
		{:else if activeItem === "Add new poll"}
			<p>Add new poll page goes here</p>
		{/if}
	
</main>
<Footer/>

<style>
	main {
		width: 90%;
		max-width: 700px;
		margin: 40px auto;
	}

</style>