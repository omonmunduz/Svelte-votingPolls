<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
	import Tabs from './shared/Tabs.svelte';
	import NewPollForm from './components/NewPollForm.svelte';
	import PollList from './components/PollList.svelte';

	let items = ["Current Polls", "Add new poll"];
	let activeItem = "Current Polls";

	let polls = [
    {
      id: 1,
      question: 'Python or JavaScript?',
      answerA: 'Python',
      answerB: 'JavaScript',
      votesA: 9,
      votesB: 15,
    },
  ];

	function tabChange(e) {
		activeItem = e.detail;
	}
	function addPoll(e){
		const poll = e.detail;
		polls = [poll, ...polls];
		activeItem = "Current Polls";
	}
	function handleVote(e) {
		const {option, id} = e.detail;
		const copiedPolls = [...polls];
		const upVotedPoll = copiedPolls.find(poll => poll.id === id);
		if(option === 'a') {
			upVotedPoll.votesA++
		}else{
			upVotedPoll.votesB++
		}
		polls = copiedPolls;
	}
</script>

<main>
	<Header/>
	<Tabs {activeItem} {items} on:tabChange = {tabChange}/>
		{#if activeItem === "Current Polls"}
			<PollList {polls} on:vote = {handleVote}/>
		{:else if activeItem === "Add new poll"}
			<NewPollForm on:addPoll={addPoll}/>
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