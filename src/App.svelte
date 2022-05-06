<script lang="ts">
  let people = [
    { id: 1, name: 'Zé Lucas', stack: 'TS' },
    { id: 2, name: 'John Doe', stack: 'JS' },
    { id: 3, name: 'Jane Doe', stack: 'Go' },
  ];

  const removePerson = (id: number): void => {
    people = people.filter((person) => person.id !== id);
  };

  let num = 5;
</script>

{#if num > 20}
  <p>Number is greater than 20</p>
{:else if num > 5}
  <p>Number is greater than 5</p>
{:else}
  <p>Not greater than 5</p>
{/if}

<main>
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
