<script>
	let people = [
		{ name: 'yoshi', beltColor: 'black', age: 25, id: 1 },
		{ name: 'mario', beltColor: 'orange', age: 45, id: 2 },
		{ name: 'luigi', beltColor: 'brown', age: 35, id: 3 }
	];

	const handleClick = (id) => {
		people = people.filter((person) => person.id != id);
	};

	let num = 5;
</script>

{#if num > 20}
	<p>Warning</p>
{:else if num > 5}
	<p>rawr</p>
{:else}
	<p>no</p>
{/if}

<main class="w-screen h-screen">
	<div class="">
		{#each people as person (person.id)}
			<div class="w-fit h-fit p-2 m-2 bg-red-400">
				<h1>{person.name}</h1>
				<p>{person.age}</p>
				<p>{person.beltColor}</p>
				{#if person.beltColor === 'black'}
					<p>Master</p>
				{/if}
				<button
					on:click={() => {
						handleClick(person.id);
					}}>Delete</button
				>
			</div>
		{:else}
			<p>There are no people to show</p>
		{/each}
	</div>
</main>
