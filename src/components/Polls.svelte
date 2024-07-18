<script>
	import { createEventDispatcher } from 'svelte';
	let dispatch = createEventDispatcher();

	export let id;
	export let title;
	export let totalVotes = 0;
	export let firstChoice;
	export let secondChoice;
	export let firstChoiceVotes = 0;
	export let secondChoiceVotes = 0;
	let percentageFirstChoice;
	let percentageSecondChoice;
	$: {
		totalVotes = firstChoiceVotes + secondChoiceVotes;
		totalVotes;
		percentageFirstChoice = Math.floor((firstChoiceVotes / totalVotes) * 100);
		percentageSecondChoice = Math.floor((secondChoiceVotes / totalVotes) * 100);
		console.log(percentageFirstChoice, percentageSecondChoice);
	}

	const handleVote = (option) => {
		dispatch('votePoll', { option, id });
	};
	const handleDelete = () => {
		dispatch('deletePoll', id);
	};
</script>

<div class="flex w-full max-w-lg flex-col gap-2 bg-white p-4">
	<h1 class="text-xl font-bold">{title}</h1>
	<p class="mb-4 opacity-50">Total Votes : {totalVotes}</p>
	<button
		class="border-l-4 border-red-500 bg-slate-50 px-6 py-2 text-left"
		on:click={() => {
			handleVote(firstChoice);
		}}>{firstChoice} ({firstChoiceVotes} Votes)</button
	>
	<div class="bg-red"></div>
	<button
		class="mb-4 border-l-4 border-green-500 bg-slate-50 px-6 py-2 text-left"
		on:click={() => {
			handleVote(secondChoice);
		}}
	>
		{secondChoice} ({secondChoiceVotes} Votes)</button
	>
	<button class="bg-red-500 px-4 py-2 font-bold text-white" on:click={handleDelete}>Delete</button>
</div>
