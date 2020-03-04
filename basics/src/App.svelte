<script>
  import CustomInput from "./CustomInput.svelte";
  import Toggle from "./Toggle.svelte";
  import { isValidEmail } from "./validation";

  let val = "boh";
  let price = "0";
  let selectedOption = 1;
  let agreed;
  let favColor = "bloo";
  let favCat = ["tiger"];
  let singleFavColor = "blue";
  let usernameInput;
  let someDiv;
  let CustomInputVal;
  let enteredEmail = "";
  let formIsValid = false;

  $: if (isValidEmail(enteredEmail)) {
    formIsValid = true;
  } else {
    formIsValid = false;
  }

  $: console.log(val);
  $: console.log(selectedOption);
  $: console.log(price);
  $: console.log(agreed);
  $: console.log(favColor);
  $: console.log(favCat);
  $: console.log(singleFavColor);
  $: console.log(CustomInputVal);

  function setValue(event) {
    val = event.target.value;
  }

  function saveData() {
    // console.log(document.querySelector('#username').value)
    console.log(usernameInput.value);
    console.dir(someDiv);
    CustomInputVal.empty();
  }
</script>

<style>
.invalid {
  border:1px solid red;
}
</style>

<!-- <input type="text" value={val} on:input={setValue}> -->
<!-- <input type="text" bind:value={val}> -->
<CustomInput bind:val bind:this={CustomInputVal} />
<Toggle bind:chosenOption={selectedOption} />

<input type="number" bind:value={price} />

<label>
  <input type="checkbox" bind:checked={agreed} />
  Agree to terms
</label>

<h1>Favorite color</h1>
<label>
  <input type="radio" value="yello" name="color" bind:group={favColor} />
  Yello
</label>
<label>
  <input type="radio" value="bloo" name="color" bind:group={favColor} />
  Bloo
</label>
<label>
  <input type="radio" value="black" name="color" bind:group={favColor} />
  Black
</label>

<h1>Favorite cat</h1>
<label>
  <input type="checkbox" value="cheshire" name="color" bind:group={favCat} />
  Cheshire
</label>
<label>
  <input type="checkbox" value="tiger" name="color" bind:group={favCat} />
  Tiger
</label>
<label>
  <input type="checkbox" value="puma" name="color" bind:group={favCat} />
  Puma
</label>

<select bind:value={singleFavColor}>
  <option value="green">Green</option>
  <option value="red">Red</option>
  <option value="blue">Blue</option>
</select>

<input type="text" id="username" bind:this={usernameInput} />
<button on:click={saveData}>Save</button>

<div bind:this={someDiv} />

<form on:submit|preventDefault>
  <input
    type="email"
    bind:value={enteredEmail}
    class={isValidEmail(enteredEmail) ? "" : "invalid"} />
  <button type="submit" disabled={!formIsValid}>Save</button>
</form>
