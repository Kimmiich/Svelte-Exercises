<script>
export let movie = {};
import { createEventDispatcher } from 'svelte';

const dispatch = createEventDispatcher();

function toggleSeen(evt) {
 dispatch('click', {
     id: evt.target.id

 })
}

</script>

<style>
    li {
        list-style-type: none;
        margin: 10px;
        padding: 10px;
        max-width: 300px;
        box-shadow: 0 0 3px rgba(114, 114, 114, 0.63);
    }
    button {
        border-radius: 5px;
    }
   button.true {
       background: rgb(247, 70, 70);
   }
   button.false {
       background: rgb(25, 168, 25);
   }
    img {
        max-width: 180px;
    }
</style>

<li>
    <img src={movie.img} alt="moviepic"/>
    <h2>{movie.title}</h2>
    <p>{movie.genre} || {movie.release_year}</p>
    <button id={movie.id} on:click={toggleSeen} class={movie.seen}>
        {#if movie.seen}
        Not seen
        {:else}
        Seen
        {/if}
    </button>
</li>