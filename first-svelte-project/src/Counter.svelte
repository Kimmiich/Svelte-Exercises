<script>
    export let userName = '';
    export let counter = 0;

const handleClick = () => {
counter ++;
}
    
</script>

<style>
h1 {
    color: blue;
}

</style>

<div>
    <h1>Counter</h1>
    Hej {userName}, du har klickat {counter} gånger på knappen!
    <button on:click={handleClick}>Klick</button>
</div>