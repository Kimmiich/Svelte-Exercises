<script>
    export let title = '';
    export let genre = '';
    export let release_year = '';
    export let img = '';

    const onSubmit = (evt) => {
        evt.preventDefault();
        let newMovie = {
            "title": evt.target.title.value,
            "genre": evt.target.genre.value,
            "release_year": evt.target.release_year.value,
            "seen": false,
            "img": "./images/generic_movie.jpg"
        }

        console.log("Formsubmit: ", newMovie)



        fetch("http://localhost:3000/movies", {
            method: "post",
            headers: {
                "Content-type": "application/json"
            },
            body: JSON.stringify(newMovie)
        })
        .then(res => res.json())
        .then(data => console.log("data", data))
        .catch(err => console.log("error", err))

    }

</script>

<style></style>

<form on:submit={onSubmit}>
    <input type="text" placeholder="Title" id="title" bind:value={title}>
    <input type="text" placeholder="Genre" id="genre" bind:value={genre}>
    <input type="text" placeholder="Release year" id="release_year" bind:value={release_year}>
    <input type="file" accept="image/jpg" id="img" bind:value={img}/>
    <button>Spara</button>
</form>