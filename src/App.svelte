<script lang="ts">
  import Modal from './Modal.svelte';

  let showModal = false;
  let isPromo = false;

  const toggleModal = (): void => {
    showModal = !showModal;
  };

  let people = [
    { id: 1, name: 'Zé Lucas', stack: 'TS' },
    { id: 2, name: 'John Doe', stack: 'JS' },
    { id: 3, name: 'Jane Doe', stack: 'Go' },
  ];

  const removePerson = (id: number): void => {
    people = people.filter((person) => person.id !== id);
  };
</script>

<Modal
  on:click={toggleModal}
  message="Hey, I'm a prop value"
  {isPromo}
  {showModal}
/>
<main>
  <button on:click={toggleModal}>Open Modal</button>

  {#each people as person (person.id)}
    <div>
      <h4>{person.name} - {person.stack}</h4>
      {#if person.stack === 'TS'}
        <p>Boa sorte</p>
      {/if}
      <button on:click={() => removePerson(person.id)}>Delete</button>
    </div>
  {:else}
    <h4>There are no people to show...</h4>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
