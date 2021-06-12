<script>
  export let autofocus = false;
  export let dataset = [];

  import { onMount } from 'svelte';

  let input = undefined;
  let inputValue = '';

  onMount(() => {
    if(autofocus) {
      input.focus();
    }
  })

  $: filteredDataset = dataset.filter((datasetItem) =>
    datasetItem.toLowerCase().includes(inputValue.toLowerCase())
  );
</script>

<input bind:this={input} placeholder='Search' type='search' bind:value={inputValue} />

<!-- Can be overwritten by the consumer -->
<slot filteredDataset={filteredDataset}>
  <ul>
    {#each filteredDataset as datasetItem}
      <li>{datasetItem}</li>
    {/each}
  </ul>
</slot>

<style>
  ul {
    list-style: none;
  }
  
  input {
    margin-bottom: 1rem;
  }
</style>