<script>
  let searchVal = "";

  function handleSearch() {
    console.log("Search term:", searchVal);
  }
</script>

<div class="search-bar">
  <input
    type="text"
    bind:value={searchVal}
    placeholder="Search..."
    on:input={handleSearch}
  />
</div>

<style>
  .search-bar {
    margin: 10px;
  }
</style>
