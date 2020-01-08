<script>
  import { tick } from "svelte";
  import Product from "./Product.svelte";
  import Modal from "./Modal.svelte";

  let products = [
    {
      id: "p1",
      title: "a book",
      price: 9.99
    }
  ];

  let text = "dummy text";

  let showModal = false;
  let closeable = false;

  function addToCart(event) {
    console.log(event.detail);
  }

  function deleteProduct(event) {
    console.log(event.detail);
  }

  function transform(event) {
    if (event.which !== 9) {
      return;
    }
    event.preventDefault();

    const selectionStart = event.target.selectionStart;
    const selectionEnd = event.target.selectionEnd;
    const value = event.target.value;

    text =
      value.slice(0, selectionStart) +
      value.slice(selectionStart, selectionEnd).toUpperCase() +
      value.slice(selectionEnd);

    // prevent cursor from jumping to the end of the text
    tick().then(() => {
      event.target.selectionStart = selectionStart;
      event.target.selectionEnd = selectionEnd;
    })
  }
</script>

{#each products as product}
  <Product {...product} on:add-to-cart={addToCart} on:delete={deleteProduct} />
{/each}

<button on:click={() => (showModal = true)}>Show modal</button>

{#if showModal}
  <Modal
    on:cancel={() => (showModal = false)}
    on:close={() => (showModal = false)}
    let:didAgree={closeable}>
    <h1 slot="header">Heyo</h1>
    <p>Content</p>
    <button
      on:click={() => (showModal = false)}
      slot="footer"
      disabled={!closeable}>
      Confirm
    </button>
  </Modal>
{/if}

<textarea rows="5" value={text} on:keydown={transform} />
