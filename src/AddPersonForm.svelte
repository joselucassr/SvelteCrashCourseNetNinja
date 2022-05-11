<script lang="ts">
  let name: string;
  let beltColor: string;
  let age: number;
  let skills: string[] = [];

  const handdleSubmit = (): void => {
    console.log(name, beltColor, age, skills);
  };
</script>

<form on:submit|preventDefault={handdleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="number" placeholder="age" bind:value={age} />

  <strong>Skills:</strong>
  <label>
    <input type="checkbox" bind:group={skills} value="fighting" /> Fighting
  </label>
  <label>
    <input type="checkbox" bind:group={skills} value="sneaking" /> Sneaking
  </label>
  <label>
    <input type="checkbox" bind:group={skills} value="running" /> Running
  </label>

  <strong>Belt Color</strong>
  <br />
  <select bind:value={beltColor}>
    <option value="black">black</option>
    <option value="orange">orange</option>
    <option value="brown">brown</option>
    <option value="white">white</option>
  </select>

  <br />

  <button type="submit">Add Person</button>
</form>

<style></style>
