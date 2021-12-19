<script>
    let user_name="";
    let gender="";
    async function getGender() {
    fetch('https://api.genderize.io/?name=' + user_name)
        .then((response) => response.json())
        .then((data) => {
        user_name = data.name; // Path for temperature
        gender = data.gender; // Path for description
	});
}
</script>

<h1>Guess Gender</h1>

<form on:submit|preventDefault={getGender}>
    <label for="Name">Name:</label>
    <input id="user_name" bind:value={user_name} type="text" />
    <button type="submit">Check</button>
</form>

<p>Gender: {gender}</p>