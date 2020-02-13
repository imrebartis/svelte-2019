<script>
  import CustomInput from "./CustomInput.svelte";
  import Toggle from "./Toggle.svelte";

  let val = "boh";
  let price = "0";
  let selectedOption = 1;
  let agreed;
  let favColor = "bloo";
  let favCat = ["tiger"];
  let singleFavColor = "blue";

  $: console.log(val);
  $: console.log(selectedOption);
  $: console.log(price);
  $: console.log(agreed);
  $: console.log(favColor);
  $: console.log(favCat);
  $: console.log(singleFavColor);

  function setValue(event) {
    val = event.target.value;
  }
</script>

<!-- <input type="text" value={val} on:input={setValue}> -->
<!-- <input type="text" bind:value={val}> -->
<CustomInput bind:val />
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
