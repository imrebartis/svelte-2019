<script>
  let val = "boh";

  $: console.log(val);

  function setValue(event) {
    val = event.target.value;
  }
</script>

<!-- <input type="text" value={val} on:input={setValue}> -->
<input type="text" bind:value={val}>