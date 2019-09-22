<script>
  import Product from "./Product.svelte";

  function addToCart(event) {
    console.log(event.detail);
  }

  function deleteProduct(event) {
    console.log(event.detail);
  }
</script>

<Product
  productTitle="a book"
  on:add-to-cart={addToCart}
  on:delete={deleteProduct} />
