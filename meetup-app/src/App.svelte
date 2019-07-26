<script>
  import Header from './UI/Header.svelte';
  import MeetupItem from './Meetups/MeetupItem.svelte';

  const meetups = [
      {
        id: 'm1',
        title: 'Coding Bootcamp',
        subtitle: 'learn to code in 1 sec',
        description: 'Organic XOXO church-key kitsch neutra subway tile cray meggings edison bulb vegan.',
        imageUrl: 'https://picsum.photos/200/300',
        address: '27th Nördern Road, 23323, Nörd Yörk',
        contactEmail: 'code@test.com'
      },
      {
        id: 'm1',
        title: 'Chill 4ever',
        subtitle: 'learn how to chill in 1 sec',
        description: 'Jianbing tumblr tattooed, yr vinyl microdosing franzen synth cray cred cardigan pug. Literally vaporware art party, blue bottle listicle ethical single-origin coffee aesthetic live-edge fingerstache.',
        imageUrl: 'https://picsum.photos/200/300',
        address: '27th Chilly Road, 23323, Chill Fork',
        contactEmail: 'chill@test.com'
      }

  ];
</script>

<style>
  #meetups {
    margin-top: 5rem;
  }
</style>

<Header />

<section id="meetups"></section>

{#each meetups as meetup}
  <MeetupItem />
{/each}