<script>
    export let first_name = '';
    export let last_name = '';
    export let email = '';

    $: console.log("firstname: " + first_name);

    const onSubmit = (evt) => {
        evt.preventDefault();

        let newUser = {
            "first_name": evt.target.first_name.value,
            "last_name": evt.target.last_name.value,
            "email": evt.target.email.value
        }

        console.log("Formsubmit: ", newUser)

        fetch("http://localhost:3000/users", {
            method: "post",
            headers: {
                "Content-type": "application/json"
            },
            body: JSON.stringify(newUser)
        })
        .then(res => res.json())
        .then(data => console.log("data", data))
        .catch(err => console.log("error", err))

    }
</script>

<style>

</style>

<form on:submit={onSubmit}>
    <input type="text" placeholder="Firstname" id="first_name" bind:value={first_name}>
    <input type="text" placeholder="Lastname" id="last_name" bind:value={last_name}>
    <input type="text" placeholder="Email" id="email" bind:value={email}>
    <button>Spara</button>
</form>