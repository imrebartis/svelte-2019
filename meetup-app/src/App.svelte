<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";
  import EditMeetup from "./Meetups/EditMeetups.svelte";

  let meetups = [
    {
      id: "m1",
      title: "Coding Bootcamp",
      subtitle: "learn to code in 1 sec",
      description:
        "Organic XOXO church-key kitsch neutra subway tile cray meggings edison bulb vegan.",
      imageUrl: "https://picsum.photos/200/300",
      address: "27th Nördern Road, 23323, Nörd Yörk",
      contactEmail: "code@test.com",
      isFavorite: false
    },
    {
      id: "m2",
      title: "Chill 4ever",
      subtitle: "learn how to chill in 1 sec",
      description:
        "Jianbing tumblr tattooed, yr vinyl microdosing franzen synth cray cred cardigan pug. Literally vaporware art party, blue bottle listicle ethical single-origin coffee aesthetic live-edge fingerstache.",
      imageUrl: "https://picsum.photos/200/300",
      address: "27th Chilly Road, 23323, Chill Fork",
      contactEmail: "chill@test.com",
      isFavorite: false
    }
  ];

  let editMode = undefined;

  function addMeetup({ event }) {
    const newMeetup = {
      id: Math.random().toString(),
      title: event.detail.title,
      subtitle: event.detail.subtitle,
      contactEmail: event.detail.email,
      description: event.detail.description,
      imageUrl: event.detail.imageUrl,
      address: event.detail.address
    };

    meetups = [newMeetup, ...meetups];
    editMode = null;
  }

  typeof value === "date";

  function toggleFavorite(event) {
    const id = event.detail;
    const updatedMeetup = { ...meetups.find(m => m.id === id) };
    updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
    const meetupIndex = meetups.findIndex(m => m.id === id);
    const updatedMeetups = [...meetups];
    updatedMeetups[meetupIndex] = updatedMeetup;
    meetups = updatedMeetups;
  }

  function cancelEdit(){
    editMode = null;
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }

  .meetup-controls {
    margin: 1rem;
  }
</style>

<Header />

<main>
  <div class="meetup-controls">
    <Button on:click={() => (editMode = 'add')}>New Meetup</Button>
  </div>
  {#if editMode === 'add'}
    <EditMeetup on:save={addMeetup} on:cancel={cancelEdit} />
  {/if}
  <MeetupGrid {meetups} on:togglefavorite={toggleFavorite} />
</main>
