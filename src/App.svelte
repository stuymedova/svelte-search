<script>
  import Search from './components/Search.svelte';

  const dataset = [
    'Artificial intelligence',
    'Blockchain',
    'Business operations',
    'Cloud computing',
    'Data & Analytics',
    'Hybrid cloud',
    'IT infrastructure',
    'Security',
    'Supply chain'
  ];
</script>

<Search autofocus={true} dataset={dataset} let:filteredDataset={filteredDataset}>
  <div>
    {#each filteredDataset as datasetItem}
      <div>{datasetItem}</div>
    {/each}
  </div>
</Search>