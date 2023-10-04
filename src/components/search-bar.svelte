<script>
  let searchTerm = "";

  function handleSearch() {
    // Implement your search logic here
    console.log("Search term:", searchTerm);
  }
</script>

<div class="search-bar">
  <input
    type="text"
    bind:value={searchTerm}
    placeholder="Search..."
    on:input={handleSearch}
  />
</div>

<style>
  .search-bar {
    margin: 10px;
  }
</style>
