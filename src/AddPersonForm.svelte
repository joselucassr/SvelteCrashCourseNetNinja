<script lang="ts">
  import { createEventDispatcher } from 'svelte';

  import type { IPerson } from './types';

  let dispatch = createEventDispatcher();

  let name: string;
  let stack: string;
  let age: number;
  let skills: string[] = [];

  const handdleSubmit = (): void => {
    const person: IPerson = {
      name,
      stack,
      age,
      skills,
      id: Math.random(),
    };

    dispatch('addPerson', person);
  };
</script>

<form on:submit|preventDefault={handdleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="number" placeholder="age" bind:value={age} />

  <strong>Skills:</strong>
  <label>
    <input type="checkbox" bind:group={skills} value="front-end" /> Front-end
  </label>
  <label>
    <input type="checkbox" bind:group={skills} value="back-end" /> Back-end
  </label>
  <label>
    <input type="checkbox" bind:group={skills} value="computer science" /> Computer
    science
  </label>

  <strong>Stack</strong>
  <br />
  <select bind:value={stack}>
    <option value="TS">TS</option>
    <option value="JS">JS</option>
    <option value="PY">PY</option>
    <option value="C#">C#</option>
  </select>

  <br />

  <button type="submit">Add Person</button>
</form>

<style></style>
