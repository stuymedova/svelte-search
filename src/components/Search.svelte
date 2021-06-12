<script>
  export let dataset = [];

  let input = undefined;
  let inputValue = '';

  $: filteredDataset = dataset.filter((datasetItem) =>
    datasetItem.toLowerCase().includes(inputValue.toLowerCase())
  );
  $: console.log(filteredDataset);
</script>

<input bind:this={input} type='search' placeholder='Search' bind:value={inputValue} />

<!-- Can be overwritten by the consumer -->
<slot {filteredDataset}>
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
</style>