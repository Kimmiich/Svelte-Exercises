<script>
import { onMount } from "svelte";
import User from './User.svelte'


export let users = [];

onMount(() => {

    setTimeout(() => {
        fetch("http://localhost:3000/users")
        .then(res => res.json())
        .then(data => {
            users = data;
        })
    }, 2000)
    
})

</script>

<style>

</style>

<div>
    {#each users as user}
    <User {user} />
    {:else}
    <div>Hämtar användare</div>
    {/each}
</div>