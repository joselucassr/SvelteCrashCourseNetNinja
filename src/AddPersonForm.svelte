<script lang="ts">
  let name: string;
  let beltColor: string;
  let age: number;
  // let fighting = false;
  // let sneaking = false;
  // let running = false;
  let skills: string[] = [];

  const handdleSubmit = (): void => {
    console.log(name, beltColor, age, skills);
  };
</script>

<form on:submit|preventDefault={handdleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="text" placeholder="belt color" bind:value={beltColor} />
  <input type="number" placeholder="age" bind:value={age} />
  <label>Skills:</label>
  <!-- <input type="checkbox" bind:checked={fighting} /> Fighting <br />
  <input type="checkbox" bind:checked={sneaking} /> Sneaking <br />
  <input type="checkbox" bind:checked={running} /> Running <br /> -->

  <input type="checkbox" bind:group={skills} value="fighting" /> Fighting <br />
  <input type="checkbox" bind:group={skills} value="sneaking" /> Sneaking <br />
  <input type="checkbox" bind:group={skills} value="running" /> Running <br />

  <button type="submit">Add Person</button>
</form>

<style></style>
