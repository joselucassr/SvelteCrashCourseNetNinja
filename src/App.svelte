<script lang="ts">
  import type { IPerson } from './types';
  import Modal from './Modal.svelte';
  import AddPersonForm from './AddPersonForm.svelte';

  let showModal = false;
  let isPromo = false;

  const toggleModal = (): void => {
    showModal = !showModal;
  };

  let people: IPerson[] = [
    { id: 1, name: 'Zé Lucas', stack: 'TS', age: 21 },
    { id: 2, name: 'John Doe', stack: 'JS', age: 35 },
    { id: 3, name: 'Jane Doe', stack: 'Go', age: 33 },
  ];

  const removePerson = (id: number): void => {
    people = people.filter((person) => person.id !== id);
  };

  const addPerson = (e): void => {
    const person: IPerson = e.detail;
    people = [person, ...people];

    toggleModal();
  };
</script>

<Modal on:click={toggleModal} {isPromo} {showModal}>
  <AddPersonForm on:addPerson={addPerson} />
</Modal>
<main>
  <button on:click|once={toggleModal}>Open Modal</button>

  {#each people as person (person.id)}
    <div>
      <h4>{person.name} - {person.stack}</h4>
      <p>{person.age} years old</p>
      {#if person.skills}
        {#each person.skills as skill (skill)}
          <p><strong>{skill}</strong></p>
          {' '}
        {/each}

        <br />
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
