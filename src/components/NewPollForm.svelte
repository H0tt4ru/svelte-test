<script>
	import { createEventDispatcher } from 'svelte';
	let dispatch = createEventDispatcher();

	let title;
	let firstChoice;
	let secondChoice;

	const handleSubmit = () => {
		const poll = {
			id: Math.random(),
			title,
			firstChoice,
			secondChoice,
			firstChoiceVotes: 0,
			secondChoiceVotes: 0
		};
		dispatch('addPoll', poll);
		title = '';
		firstChoice = '';
		secondChoice = '';
	};
</script>

<div class="flex w-full justify-center">
	<form
		class="mx-4 flex w-full max-w-xl flex-col gap-2 text-lg"
		on:submit|preventDefault={handleSubmit}
	>
		<label for="Title">Title</label>
		<input class="mb-4 px-4 py-2" type="text" placeholder="Title" bind:value={title} />
		<label for="First Choice">First Choice</label>
		<input class="mb-4 px-4 py-2" type="text" placeholder="First Choice" bind:value={firstChoice} />
		<label for="Second Choice">Second Choice</label>
		<input
			class="mb-4 px-4 py-2"
			type="text"
			placeholder="Second Choice"
			bind:value={secondChoice}
		/>
		<button class="bg-indigo-500 px-4 py-2 font-bold text-white">Submit Polls</button>
	</form>
</div>
