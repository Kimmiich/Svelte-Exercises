<script>
    //This import is so that we can send onsubmit event up the ladder of components
    import { createEventDispatcher } from 'svelte';

    //Simplifying how we call above function
    const dispatch = createEventDispatcher();

    //Getting variables from props passed down in app.js
	export let name;
	export let points;

    //Local variable for toggle function
	let showControls = false;

    //Function for adding points when pressing + button
	const addPoints = () => points += 1;

    //Function for removing points when pressing - button
	const removePoints = () => points -= 1;

    //Function for toggling points editors
	const toggleControls = () => (showControls = !showControls);

    //Function for deleting player, uses dispatch, value comes from button oncLick onDelete
    const onDelete = () =>  dispatch("removeplayer", name);

</script>

<style>

	h1 {
		color: #204f6e;
	}

	h3 {
		margin-bottom: 10px;
	}
</style>


	<div class="card">
		<h1>
			{name}
			<button class="btn btn-sm" on:click={toggleControls}>
				{#if showControls}-{:else}+{/if}
			</button>
            <button class="btn btn-danger btn-sm" on:click={onDelete}>
                X
            </button>
		</h1>
		<h3>Points: {points}</h3>
		{#if showControls}
		<button class="btn" on:click={addPoints}>+</button>
		<button class="btn btn-dark" on:click={removePoints}>-</button>
		<input type="number" bind:value={points} />
		{/if}
	</div>

