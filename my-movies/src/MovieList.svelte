<script>
    import Movie from './Movie.svelte';
    import { onMount } from 'svelte';
    export let movies = [];

    onMount(() => {

setTimeout(() => {
    fetch("http://localhost:3000/movies")
    .then(res => res.json())
    .then(data => {
        console.log(data)
        movies = data;
    })
}, 2000)


})

function handleClick(evt) {
    let id = evt.detail.id;

    let value =movies.find((movie) => 
      movie.id == id);

      console.log(value)


    fetch("http://localhost:3000/movies/" + value.id, {
        method: 'PATCH',
        body: JSON.stringify({
            "seen": !value.seen
        }),
        headers: {
            "Content-type": "application/json"
        }
    })
    .then(resp => resp.json())
    .then(newData => console.log(newData))
    
}

</script>

<style>
ul {
    max-width: 1200px;
    margin: auto;
    display: flex;
    flex-flow: row wrap;
    justify-content: center;
}
</style>

<ul>
{#each movies as movie}
<Movie {movie} on:click={handleClick} />
{:else}
<div>Getting movies...</div>
{/each}
</ul>