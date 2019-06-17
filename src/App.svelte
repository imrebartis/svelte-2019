<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Mix";
  let title = "";
  let image = "";
  let description = "";
  let page = 1;

  $: uppercaseName = name.toUpperCase();
  $: console.log(name);
  $: if (name === "Fix") {
    console.log("it works");
    page = 1000;
  }

  function incrementPage() {
    page += 1;
  }

  function changeName() {
    name = "Fix";
  }

  function nameInput(event) {
    const enteredValue = event.target.value;
    name = enteredValue;
  }
</script>

<style>
  h1 {
    color: purple;
  }
</style>

<h1>Hello {uppercaseName}, my page is {page}!</h1>
<button on:click={incrementPage}>Change page</button>
<!-- <button on:click='{changeName}'>Change name</button> -->
<!-- <input type="text" value="{name}" on:input="{nameInput}"> -->
<input type="text" bind:value={name} />
<input type="text" bind:value={title} />
<input type="text" bind:value={image} />
<textarea rows="3" bind:value={description} />
<ContactCard 
	userName={name}
	jobTitle={title}
	{description}
	userImage={image} />
