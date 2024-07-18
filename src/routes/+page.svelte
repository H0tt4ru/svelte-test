<script>
	import Header from '../components/Header.svelte';
	import Footer from '../components/Footer.svelte';
	import Choice from '../components/Choice.svelte';
	import CurrentPolls from '../components/CurrentPolls.svelte';
	import NewPollForm from '../components/NewPollForm.svelte';

	let activeChoice;
	let polls = [];
	const addPoll = (e) => {
		const poll = e.detail;
		polls = [...polls, poll];
		console.log('Create poll : ', poll);
	};
	const deletePoll = (e) => {
		const id = e.detail;
		polls = polls.filter((poll) => poll.id != id);
	};
	const votePoll = (e) => {
		const { option, id } = e.detail;
		let tempPolls = polls;
		let votedPoll = tempPolls.find((poll) => poll.id == id);
		console.log(votedPoll);
		if (option == votedPoll.firstChoice) {
			votedPoll.firstChoiceVotes++;
		} else if (option == votedPoll.secondChoice) {
			votedPoll.secondChoiceVotes++;
		}
		polls = tempPolls;
	};
</script>

<main class="min-h-screen w-screen bg-slate-50">
	<Header />
	<Choice bind:activeChoice />
	{#if activeChoice == 1}
		<CurrentPolls {polls} on:deletePoll={deletePoll} on:votePoll={votePoll} />
	{:else if activeChoice == 2}
		<NewPollForm on:addPoll={addPoll} />
	{:else}
		<div class="flex w-full justify-center">
			<h1 class="text-xl font-bold">Integer Error</h1>
		</div>
	{/if}
	<Footer />
</main>
