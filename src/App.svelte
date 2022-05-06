<script lang="ts">
  let name = 'World';

  const changeName = (e: Event): void => {
    let target = e.target as HTMLInputElement;
    let inputValue = target.value;
    name = inputValue;

    if (!inputValue) {
      name = 'World';
    }
  };
</script>

<main>
  <h1>Hello {name}!</h1>
  <p>
    Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
    how to build Svelte apps.
  </p>

  <input type="text" on:input={changeName} value={name} />
  <input type="text" bind:value={name} />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
