<script>
  import MeetUpItem from './MeetUpItem.svelte'

  export let meetups 
</script>

<style>
  #meetups {
    margin-top: 1rem;
  }

  section {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 1rem;
  }

  @media (min-width: 768px) {
    section {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>

<section id='meetups'>
  {#each meetups as meetup, i (meetup.id)}
    <MeetUpItem 
      title={meetup.title}
      subtitle={meetup.subtitle}
      imageUrl={meetup.imageUrl}
      description={meetup.description}
      address={meetup.address}
      email={meetup.contactEmail}
    />
  {/each}
</section>