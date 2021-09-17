<script>
	//imports diffrent components to print in app.js
	import Navbar from './Navbar.svelte';
	import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte';

	//Original array och players, change to jsonfile, do a fetch here and set players to response data?
	let players = [
		{
			name: 'John Doe',
			points: 53
		},
		{
			name: 'Sam Smith',
			points: 45
		},
		{
			name: 'Sara Wilson',
			points: 32
		}
	];

	//This function actually changes the players array with help of a dispatcher in lower components, we catch the value of newPlayer from dispatch with evt.detail. 
	const addPlayer = (evt) => {
		const newPlayer = evt.detail;
		players = [...players, newPlayer];
	}

	//This function removes a player with help of information from dispatcher, when working with db or Json detail should be id
	const removePlayer = (evt) => {
		players = players.filter(player => player.name !== evt.detail);
	}

</script>

<style>

</style>

<Navbar />
<div class="container">
	<AddPlayer on:addplayer={addPlayer}/>
	{#if players.length === 0}
	<p>No players...</p>
	{:else}
		{#each players as player}
		<Player name={player.name} points={player.points} on:removeplayer={removePlayer}/>
		{/each}
	{/if}
</div>

