<script>
  import Header from './UI/Header.svelte'
  import MeetUpItems from './Meetups/MeetupGrid.svelte'
  import TextInput from './UI/TextInput.svelte'
  import Button from './UI/Button.svelte'

  let title = ''
  let subtitle = ''
  let description = ''
  let imageUrl = ''
  let address = ''
  let email = ''

  let meetups = [
    {
      id: 'm1',
      title: 'Coding Bootcamp',
      subtitle: 'Learn to code in 2 hours',
      description:
        "In this meetup, we'll have expertes that teach you how to code with Svelte.",
      imageUrl: 'https://miro.medium.com/max/1200/0*T6pKJjgoPIBy_u-_.png',
      address: '27th Nerd Nerd Road, 752 New York',
      contactEmail: 'code@test.com',
    },
    {
      id: 'm2',
      title: 'Swim Together',
      subtitle: "Let's swim together",
      description: 'In this meetup, it`s for people that loves to swim.',
      imageUrl:
        'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRnbGjKPgyt6EN1nHwR6iZN4rC0JxOAJfJcfNP1_7S5ReRD-Ne7CASciNqWsbgWXOBTDMc&usqp=CAU',
      address: '27th Nerd Swimg Road, 72 New York',
      contactEmail: 'swimg@test.com',
    },
  ]

  function addMetup() {
    let newMeetup = {
      id: Math.random().toString(),
      title,
      subtitle,
      description,
      imageUrl,
      address,
      contactEmail: email,
    }

    meetups = [newMeetup, ...meetups]
  }
</script>

<style>
  main {
    margin-top: 5rem;
    padding: 0 1rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>


<Header />

<main>
  <form on:submit|preventDefault={addMetup}>
    <TextInput
      type="text"
      id="title"
      label="Title"
      value={title}
      on:input={(event) => (title = event.target.value)}
    />

    <TextInput
      type="text"
      id="subtitle"
      label="Subtitle"
      value={subtitle}
      on:input={(event) => (subtitle = event.target.value)}
    />

    <TextInput
      type="text"
      id="imgUrl"
      label="Image URL"
      value={imageUrl}
      on:input={(event) => (imageUrl = event.target.value)}
    />

    <TextInput
      type="text"
      id="address"
      label="Address"
      value={address}
      on:input={(event) => (address = event.target.value)}
    />

    <TextInput
      type="email"
      id="contactEmail"
      label="Email"
      value={email}
      on:input={(event) => (email = event.target.value)}
    />

    <TextInput
      controlType="textarea"
      rows="3"
      id="descirption"
      label="Description"
      value={description}
      on:input={(event) => (description = event.target.value)}
    />

    <Button type='submit' caption='Save'/>
  </form>
  <MeetUpItems {meetups} />
</main>
