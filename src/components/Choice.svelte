<script>
	export let activeChoice = 1;
	let choices = [
		{ id: 1, value: 'Current Polls' },
		{ id: 2, value: 'Add New Poll' }
	];

	const handleClick = (id) => {
		activeChoice = id;
	};
</script>

<div class="my-10 flex w-full justify-center space-x-10 text-xl">
	{#each choices as choice}
		<button
			class={`${choice.id === activeChoice ? 'border-red-500 text-red-500 opacity-100' : 'opacity-50'} border-b-2 pb-2 hover:opacity-100`}
			on:click={() => {
				handleClick(choice.id);
			}}>{choice.value}</button
		>
	{/each}
</div>
