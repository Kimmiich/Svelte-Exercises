<script>
    export let user = {};
</script>

<style>
    div {
        margin: 10px;
        padding: 10px;
        max-width: 300px;
        border: 1px solid green;
    }

</style>

<div>
    {user.first_name} {user.last_name} <br/>
    {user.email}
</div>