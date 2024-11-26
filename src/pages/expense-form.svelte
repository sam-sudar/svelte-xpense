<script>
  //   import { categoriesStore } from "../store";

  let expenseName = "";
  let selectedCategory = "";
  let amountSpent = 0;
  let expenseArray = [];
  export let categoryMessage;
  export let newsharedState;
  $: categoryMessage = $newsharedState.categoryMessage;

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
      $expenseSharedState.expenseMessage = expenseArray;

      expenseName = "";
      selectedCategory = "";
      amountSpent = 0;
    }
  }

  export let expenseSharedState;
</script>

<!-- Expense form -->

<div id="expense" class="mainExpense_div">
  <div class="form_div">
    <p id="title_p">Add Expenses</p>
    <form on:submit={handleEvent}>
      <label for="expense-name">Expense Name</label>
      <input
        type="text"
        id="expense-name"
        placeholder="Enter expense name"
        bind:value={expenseName}
      />

      <label for="category">Category</label>
      <select id="category" bind:value={selectedCategory}>
        {#each categoryMessage as category}
          <p>Hello {category.name}</p>
        {/each}
        {#each categoryMessage as cat}
          <option value={cat.name}>{cat.name}</option>
        {/each}
      </select>

      <label for="amount-spent">Amount Spent</label>
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
  <div class="display_div">
    <p id="title_p">Expenses</p>
    {#if expenseArray.length > 0}
      <ul>
        {#each expenseArray as exp}
          <li>
            <div id="listItems_div">
              <div id="list_div">
                <p>{exp.name}</p>
                <p>{exp.category}</p>
              </div>

              <p id="expAmount_p">${exp.amount}</p>
            </div>
          </li>
        {/each}
      </ul>
    {:else}
      <p>No expenses added yet.</p>
    {/if}
  </div>
</div>

<style>
  .mainExpense_div {
    width: 83%;
    height: 740px;
    background-color: #66fcf1;
    color: #0b0c10;
    display: flex;
    margin-left: 250px;
    align-items: center;
  }

  .form_div {
    width: 60%;
    height: 100%;
    background-color: #0b0c10;
    color: #66fcf1;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  #title_p {
    font-size: 4.5rem;
    font-weight: bolder;
    margin: 30px 0px;
  }

  form {
    width: 80%;
    height: 540px;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #66fcf1;
    color: #0b0c10;
    font-weight: bold;
    margin-bottom: 50px;
    padding: 30px 0px;
  }

  label {
    font-size: 2.4rem;
  }

  input {
    height: 45px;
    width: 50%;
    margin-bottom: 25px;
    background-color: #1f2833;
    border: 2px solid #66fcf1;
    color: #66fcf1;
    font-size: 1.2rem;
    margin-top: 15px;
    border-radius: 10px;
  }

  select {
    width: 50%;
    height: 9%;
    margin-bottom: 25px;
    background-color: #1f2833;
    border: 2px solid #66fcf1;
    color: #66fcf1;
    font-size: 1.2rem;
    margin-top: 15px;
    border-radius: 10px;
  }

  option {
    font-weight: bold;
  }

  button {
    width: 40%;
    height: 10%;
    margin-top: 25px;
    background-color: #0b0c10;
    font-size: 1.2rem;
    color: #66fcf1;
    font-weight: bold;
    border-radius: 10px;
  }
  button:hover {
    /* border: 2px solid #0b0c10; */
    color: #0b0c10;
    background-color: #66fcf1;
  }

  .display_div {
    width: 40%;
    height: 100%;
    background-color: #66fcf1;
    display: flex;
    align-items: center;
    flex-direction: column;
  }

  ul {
    width: 92%;
    padding: 0;
  }
  #listItems_div {
    width: 100%;
    height: 50px;
    display: flex;
    justify-content: space-between;
  }

  #list_div {
    display: flex;
    flex-direction: column;
  }
  p {
    margin-top: 160px;
    font-size: 1.4rem;
    font-weight: 500;
  }

  li {
    width: 96%;
    height: 50px;
    background-color: #45a29e;
    color: #0b0c10;
    font-size: 1.4rem;
    list-style: none;
    position: relative;
    padding: 10px;
  }
  li p {
    margin: 0;
  }

  li p:nth-child(1) {
    font-size: 24px;
    text-align: left;
  }

  li p:nth-child(2) {
    font-size: 16px;
  }

  li p:nth-child(3) {
    font-size: 24px;
    text-align: left;
  }
  #expAmount_p {
    font-size: 30px;
  }
</style>
