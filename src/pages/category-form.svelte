<script>
  // import ExpenseForm from "../Expense_Page/ExpenseForm.svelte";
  import { categoriesStore } from "../store/store";

  let category = "";
  let budget = 0;
  let categories = [{ name: "food", maxBudget: 4000 }];

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

      categoriesStore.set(categories);

      category = "";
      budget = 0;
    }
  }
</script>

<!-- Category form -->
<h2>Add Categories</h2>
<form on:submit={handleCategoryFormSubmit}>
  <label for="category">Category Name:</label>
  <input
    type="text"
    id="category"
    placeholder="Enter category name"
    bind:value={category}
  />

  <label for="budget">Max Budget:</label>
  <input
    type="number"
    id="budget"
    placeholder="Enter max budget"
    bind:value={budget}
  />

  <button type="submit">Add Category</button>
</form>

<h2>Categories</h2>
{#if $categoriesStore.length > 0}
  <ul>
    {#each $categoriesStore as cat (cat.name)}
      <li>
        Category: {cat.name}, Max Budget: ${cat.maxBudget}
      </li>
    {/each}
  </ul>
{:else}
  <p>No categories added yet.</p>
{/if}
