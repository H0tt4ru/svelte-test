<script>
	import Polls from './Polls.svelte';

	export let polls;
</script>

<div class="flex w-full justify-center">
	{#if polls.length > 0}
		<div class="mx-4 grid w-full max-w-6xl grid-cols-1 place-items-center gap-4 md:grid-cols-2">
			{#each polls as poll (poll.id)}
				<Polls
					id={poll.id}
					title={poll.title}
					totalVotes={poll.totalVotes}
					firstChoice={poll.firstChoice}
					secondChoice={poll.secondChoice}
					firstChoiceVotes={poll.firstChoiceVotes}
					secondChoiceVotes={poll.secondChoiceVotes}
					on:deletePoll
					on:votePoll
				/>
			{/each}
		</div>
	{:else}
		<div class="flex w-full justify-center">
			<h1 class="text-xl font-bold">There are no polls to show ...</h1>
		</div>
	{/if}
</div>
