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

  function toggleFavorite(event) {
    const id = event.detail;
    const updatedMeetup = { ...meetups.find(m => m.id === id) };
    updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
    const meetupIndex = meetups.findIndex(m => m.id === id);
    const updatedMeetups = [...meetups];
    updatedMeetups[meetupIndex] = updatedMeetup;
    meetups = updatedMeetups;
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }
</style>

<Header />

<main>
  <Button caption="New Meetup" on:click={() => (editMode = 'add')} />
  {#if editMode === 'add'}
    <EditMeetup />
  {/if}
  <MeetupGrid {meetups} on:togglefavorite={toggleFavorite} />
</main>
