<script>
  let category = "";
  let budget = 0;
  let categories = [];

  function handleCategoryFormSubmit(event) {
    event.preventDefault();

    if (category && budget > 0) {
      categories = [
        {
          name: category,
          maxBudget: budget,
        },
        ...categories,
      ];

      $newsharedState.categoryMessage = categories;

      category = "";
      budget = 0;
    }
  }
  // export let sharedState;
  export let newsharedState;
</script>

<!-- Category form -->
<div id="category" class="mainCat_div">
  <h1>Add Categories</h1>
  <form on:submit={handleCategoryFormSubmit}>
    <label for="category">Category Name</label>
    <input
      type="text"
      id="category"
      placeholder="Enter category name"
      bind:value={category}
    />

    <label for="budget">Max Budget</label>
    <input
      type="number"
      id="budget"
      placeholder="Enter max budget"
      bind:value={budget}
    />

    <button type="submit">Add Category</button>
  </form>

  <!-- <h2>Categories</h2>
  {#if categories.length > 0}
    <ul>
      {#each categories as cat (cat.name)}
        <li>
          Category: {cat.name}, Max Budget: ${cat.maxBudget}
        </li>
      {/each}
    </ul>
  {:else}
    <p>No categories added yet.</p>
  {/if} -->
</div>

<style>
  .mainCat_div {
    width: 83%;
    height: 740px;
    color: #66fcf1;
    display: flex;
    flex-direction: column;
    margin-left: 250px;
    justify-content: center;
    align-items: center;
    background-color: #0b0c10;
  }
  h1 {
    font-size: 4.5rem;
    margin: 35px 0;
  }
  form {
    background-color: #66fcf1;
    color: #0b0c10;
    font-weight: bold;
    width: 80%;
    height: 700px;
    margin-bottom: 55px;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 25px;
  }
  form label {
    font-size: 2.8rem;
    padding-top: 40px;
  }
  form input {
    background-color: #1f2833;
    border: 2px solid #66fcf1;
    color: #66fcf1;
    font-size: 1.2rem;
    height: 45px;
    width: 30%;
    margin-top: 15px;
    border-radius: 10px;
  }
  form button {
    height: 50px;
    width: 20%;
    background-color: #0b0c10;
    font-size: 1.2rem;
    margin-top: 45px;
    color: #66fcf1;
    font-weight: bold;
    border-radius: 10px;
  }
  form button:hover {
    border: 3px solid #0b0c10;
    color: #0b0c10;
    background-color: #66fcf1;
  }
</style>
