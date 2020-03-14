<script>
  import { createEventDispatcher } from "svelte";
  import TextInput from "../UI/TextInput.svelte";
  import Button from "../UI/Button.svelte";
  import Modal from "../UI/Modal.svelte";
  import { isEmpty, isValidEmail } from "../helpers/validation.js";

  let title = "";
  let titleValid = false;
  let subtitle = "";
  let subtitleValid = false;
  let email = "";
  let emailValid = false;
  let description = "";
  let descriptionValid = false;
  let address = "";
  let addressValid = false;
  let imageUrl = "";
  let imageUrlValid = false;
  let formIsValid = false;

  const dispatch = createEventDispatcher();

  function cancel() {
    dispatch("cancel");
  }

  $: titleValid = !isEmpty(title);
  $: subtitleValid = !isEmpty(subtitle);
  $: emailValid = isValidEmail(email);
  $: descriptionValid = !isEmpty(description);
  $: addressValid = !isEmpty(address);
  $: imageUrlValid = !isEmpty(imageUrl);
  $: formIsValid =
    titleValid &&
    subtitleValid &&
    emailValid &&
    descriptionValid &&
    addressValid &&
    imageUrlValid;

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
      valid={titleValid}
      validityMessage="Please enter a breathtaking title."
      value={title}
      on:input={event => (title = event.target.value)} />
    <TextInput
      id="subtitle"
      valid={subtitleValid}
      validityMessage="Please enter a breathtaking subtitle."
      label="Subtitle"
      value={subtitle}
      on:input={event => (subtitle = event.target.value)} />
    <TextInput
      id="address"
      valid={addressValid}
      validityMessage="Please enter a breathtaking address."
      label="Address"
      value={address}
      on:input={event => (address = event.target.value)} />
    <TextInput
      id="imageUrl"
      valid={imageUrlValid}
      validityMessage="Please enter a breathtaking image url."
      label="Image Url"
      value={imageUrl}
      on:input={event => (imageUrl = event.target.value)} />
    <TextInput
      id="email"
      valid={emailValid}
      validityMessage="Please enter a valid email address."
      label="Email"
      type="email"
      value={email}
      on:input={event => (email = event.target.value)} />
    <TextInput
      id="description"
      valid={descriptionValid}
      validityMessage="Please enter a breathtaking description."
      label="Description"
      controlType="textarea"
      value={description}
      rows="3"
      on:input={event => (description = event.target.value)} />
  </form>
  <div slot="footer">
    <Button type="button" mode="outline" on:click={cancel}>Cancel</Button>
    <Button type="button" on:click={submitForm} disabled={!formIsValid}>Save</Button>
  </div>
</Modal>
