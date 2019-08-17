<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";

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
    }

    meetups = [newMeetup, ...meetups];
  }
</script>

<style>
  #meetups {
    margin-top: 5rem;
  }
</style>

<Header />

<main>
  <form on:submit|preventDefault="{addMeetup}">
    <div class="form-control">
      <label for="title">Title</label>
      <input type="text" id="title" bind:value={title}>
    </div>
    <div class="form-control">
      <label for="subtitle">Subtitle</label>
      <input type="text" id="subtitle" bind:value={subtitle}>
    </div>
    <div class="form-control">
      <label for="address">Address</label>
      <input type="text" id="address" bind:value={address}>
    </div>
    <div class="form-control">
      <label for="imageUrl">Image URL</label>
      <input type="text" id="imageUrl" bind:value={imageUrl}>
    </div>
    <div class="form-control">
      <label for="email">Email</label>
      <input type="email" id="email" bind:value={email}>
    </div>
    <div class="form-control">
      <label for="description">Description</label>
      <textarea rows="3" id="description" bind:value={description}/>
    </div>
    <button type="submit">Save</button>
  </form>
  <MeetupGrid {meetups} />
</main>