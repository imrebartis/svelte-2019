<script>
  import { createEventDispatcher } from "svelte";
  import TextInput from "../UI/TextInput.svelte";
  import Button from "../UI/Button.svelte";
  import Modal from "../UI/Modal.svelte";

  let title = "";
  let subtitle = "";
  let email = "";
  let description = "";
  let address = "";
  let imageUrl = "";

  const dispatch = createEventDispatcher();

  function cancel() {
    dispatch("cancel");
  }

  function submitForm() {
    dispatch("save", {
      title,
      subtitle,
      address,
      email,
      description,
      imageUrl
    });
  }
</script>

<style>
  form {
    width: 100%;
  }
</style>

<Modal title="Edit meetup data" on:cancel>
  <form on:submit|preventDefault={submitForm}>
    <TextInput
      id="title"
      label="Title"
      valid={true}
      validityMessage="Please enter a breathtaking title."
      value={title}
      on:input={event => (title = event.target.value)} />
    <TextInput
      id="subtitle"
      label="Subtitle"
      value={subtitle}
      on:input={event => (subtitle = event.target.value)} />
    <TextInput
      id="address"
      label="Address"
      value={address}
      on:input={event => (address = event.target.value)} />
    <TextInput
      id="imageUrl"
      label="Image Url"
      value={imageUrl}
      on:input={event => (imageUrl = event.target.value)} />
    <TextInput
      id="email"
      label="Email"
      type="email"
      value={email}
      on:input={event => (email = event.target.value)} />
    <TextInput
      id="description"
      label="Description"
      controlType="textarea"
      value={description}
      rows="3"
      on:input={event => (description = event.target.value)} />
  </form>
  <div slot="footer">
    <Button type="button" mode="outline" on:click={cancel}>Cancel</Button>
    <Button type="button" on:click={submitForm}>Save</Button>
  </div>
</Modal>
