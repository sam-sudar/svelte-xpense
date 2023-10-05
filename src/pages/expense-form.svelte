<script>
  //   import { categoriesStore } from "../store";

  let expenseName = "";
  let selectedCategory = "";
  let amountSpent = 0;
  let expenseArray = [];
  let categories = ["food"];

  function handleEvent(event) {
    event.preventDefault();

    if (expenseName && selectedCategory && amountSpent > 0) {
      expenseArray = [
        {
          name: expenseName,
          category: selectedCategory,
          amount: amountSpent,
        },
        ...expenseArray,
      ];

      expenseName = "";
      selectedCategory = "";
      amountSpent = 0;
    }
  }
</script>

<!-- Expense form -->
<div>
  <h2>Add Expenses</h2>
  <form on:submit={handleEvent}>
    <label for="expense-name">Expense Name:</label>
    <input
      type="text"
      id="expense-name"
      placeholder="Enter expense name"
      bind:value={expenseName}
    />

    <label for="category">Category:</label>
    <select id="category" bind:value={selectedCategory}>
      {#each categories as cat (cat.name)}
        <option value={cat.name}>{cat.name}</option>
      {/each}
    </select>

    <label for="amount-spent">Amount Spent:</label>
    <input
      type="number"
      id="amount-spent"
      placeholder="Enter amount spent"
      bind:value={amountSpent}
    />

    <button type="submit">Add Expense</button>
  </form>
</div>

<!-- Display expenses -->
<h2>Expenses</h2>
{#if expenseArray.length > 0}
  <ul>
    {#each expenseArray as exp}
      <li>
        Expense Name: {exp.name}, Category: {exp.category}, Amount Spent: ${exp.amount}
      </li>
    {/each}
  </ul>
{:else}
  <p>No expenses added yet.</p>
{/if}

<style>
  div {
    width: 300px;
    height: 350px;
    color: #000;
    background-color: aqua;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
