<script>
    //This import is so that we can send onsubmit event up the ladder of components
    import { createEventDispatcher } from 'svelte';

    //Simplifying how we call above function
    const dispatch = createEventDispatcher();

    //object to hold the input values, that we also send with dispatcher. These values is binded to input value and automatically updates when input updates
    let player = {
        name: '',
        points: 0
    };

    //Local eventhandler that sends dispatch with a callback and object/value. evt.preventdefault is to avoid normal behavior on form submit.
    const onSubmit = (evt) => {
        evt.preventDefault();
        dispatch("addplayer", player);
        player = {
            name: '',
            points: 0
        }
    }

</script>

<form on:submit={onSubmit} class="grid-3">
    <input type="text" placeholder="Player Name" bind:value={player.name}/>
    <input type="number" bind:value={player.points}/>
    <input type="submit" class="btn btn-primary" value="Add player">
</form>