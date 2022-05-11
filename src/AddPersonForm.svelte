<script lang="ts">
  let name: string;
  let beltColor: string;
  let age: number;

  const handdleSubmit = (): void => {
    console.log(name, beltColor, age);
  };
</script>

<form on:submit|preventDefault={handdleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="text" placeholder="belt color" bind:value={beltColor} />
  <input type="number" placeholder="age" bind:value={age} />
  <button type="submit">Add Person</button>
</form>

<style></style>
