<script>
  import Product from "./Product.svelte";
</script>

<Product productTitle="a book" on:click="{() => alert('clicked')}" />
