<script>
	import Counter from './Counter.svelte';
	import Users from './Users.svelte';
	import AddForm from './AddForm.svelte';
	export const userName = 'Kimmie';
	export let name;
</script>

<main>
	<h1>Hello {name}!</h1>
	<Counter {userName}/>
	<h2>Add user</h2>
	<AddForm/>
	<h2>Look at all these users!</h2>
	<Users/>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>