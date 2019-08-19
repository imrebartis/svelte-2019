<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";

  let title = "";
  let subtitle = "";
  let email = "";
  let description = "";
  let address = "";
  let imageUrl = "";
  let meetups = [
    {
      id: "m1",
      title: "Coding Bootcamp",
      subtitle: "learn to code in 1 sec",
      description:
        "Organic XOXO church-key kitsch neutra subway tile cray meggings edison bulb vegan.",
      imageUrl: "https://picsum.photos/200/300",
      address: "27th Nördern Road, 23323, Nörd Yörk",
      contactEmail: "code@test.com"
    },
    {
      id: "m1",
      title: "Chill 4ever",
      subtitle: "learn how to chill in 1 sec",
      description:
        "Jianbing tumblr tattooed, yr vinyl microdosing franzen synth cray cred cardigan pug. Literally vaporware art party, blue bottle listicle ethical single-origin coffee aesthetic live-edge fingerstache.",
      imageUrl: "https://picsum.photos/200/300",
      address: "27th Chilly Road, 23323, Chill Fork",
      contactEmail: "chill@test.com"
    }
  ];

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title,
      subtitle,
      contactEmail: email,
      description,
      imageUrl,
      address
    };

    meetups = [newMeetup, ...meetups];
  }
</script>

<style>
  main {
    margin-top: 5rem
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<Header />

<main>
  <form on:submit|preventDefault={addMeetup}>
    <TextInput
      id="title"
      label="Title"
      type="text"
      value={title}
      on:input={event => (title = event.target.value)} />
    <TextInput
      id="subtitle"
      label="Subtitle"
      type="text"
      value={subtitle}
      on:input={event => (subtitle = event.target.value)} />
     <TextInput
      id="address"
      label="Address"
      type="text"
      value={address}
      on:input={event => (address = event.target.value)} />
     <TextInput
      id="imageUrl"
      label="Image Url"
      type="text"
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

    <button type="submit">Save</button>
  </form>
  <MeetupGrid {meetups} />
</main>
