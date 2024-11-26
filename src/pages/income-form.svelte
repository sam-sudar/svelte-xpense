<script>
  import { createEventDispatcher } from "svelte";

  let incomeAmount = 0;
  let incomeSource = "";
  let incomeFrequency = "";
  let isTicked = false;
  let nextIncomeDate = null;

  const incomeFrequencyOptions = ["Weekly", "Monthly", "Yearly"];
  let incomes = [];

  // Create an event dispatcher
  const dispatch = createEventDispatcher();

  function handleIncomeEvent(event) {
    incomeFrequency = event.target.value;
    calculateNextIncomeDate();
  }

  function calculateNextIncomeDate() {
    if (isTicked && incomeFrequency) {
      const currentDate = new Date();

      if (incomeFrequency === "Weekly") {
        currentDate.setDate(currentDate.getDate() + 7);
      } else if (incomeFrequency === "Monthly") {
        currentDate.setMonth(currentDate.getMonth() + 1);
      } else if (incomeFrequency === "Yearly") {
        currentDate.setFullYear(currentDate.getFullYear() + 1);
      }

      nextIncomeDate = currentDate;
    } else {
      nextIncomeDate = null;
    }
  }

  function handleFormSubmit(event) {
    event.preventDefault();

    if (incomeAmount && incomeSource) {
      incomes = [
        {
          amount: incomeAmount,
          source: incomeSource,
        },
        ...incomes,
      ];

      $sharedState.message = incomes;

      incomeAmount = 0;
      incomeSource = "";
      incomeFrequency = "";
      isTicked = false;

      calculateNextIncomeDate();
    }
  }

  function sendDataToParent() {
    dispatch("incomeAmountData", { message: incomeAmount });
  }

  //send data by store
  export let sharedState;

  // function updateSharedState() {

  // }
</script>

<div id="income" class="mainIncome_div">
  <div class="addInc_div">
    <label for="addIncomeAuto">Add Income Automatically</label>
    <input
      type="checkbox"
      id="addIncomeAuto"
      bind:checked={isTicked}
      on:change={calculateNextIncomeDate}
    />

    <p>Next Income Date</p>
    <p>{nextIncomeDate ? nextIncomeDate.toDateString() : ""}</p>
  </div>
  <form on:submit={handleFormSubmit}>
    <p id="title_p">INCOME</p>
    <label for="amount">Income Amount</label>
    <input
      type="number"
      id="amount"
      placeholder="Enter the income amount"
      bind:value={incomeAmount}
    />

    <label for="incomeFrequency">Income Frequency</label>
    <select
      id="incomeFrequency"
      bind:value={incomeFrequency}
      on:change={handleIncomeEvent}
    >
      {#each incomeFrequencyOptions as option}
        <option value={option}>{option}</option>
      {/each}
    </select>

    <label for="source">Source:</label>
    <input
      type="text"
      id="source"
      placeholder="Income source"
      bind:value={incomeSource}
    />

    <button type="submit">Add Income</button>
  </form>
  <div class="recent_div">
    <h1>RECENT INCOMES</h1>
    {#if incomes.length > 0}
      <ul>
        {#each incomes as income}
          <li>
            <p>Amount: ${income.amount}</p>
            <p>Source: {income.source}</p>
          </li>
        {/each}
      </ul>
    {/if}
  </div>
</div>

<style>
  .mainIncome_div {
    width: 83%;
    height: 740px;
    color: #000;
    display: flex;
    margin-left: 250px;
    justify-content: center;
    align-items: center;
    background-color: #0b0c10;
    padding-top: 9px;
    align-items: center;
  }
  #title_p {
    font-size: 4.5rem;
    font-weight: bolder;
    margin: 30px 0px 65px;
  }

  form {
    width: 48%;
    background-color: #66fcf1;
    border-radius: 10px;
    height: 700px;
    margin: 20px auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    font-weight: bold;
  }

  label {
    font-size: 1.7rem;
    margin-bottom: 5px;
  }

  select {
    width: 80%;
  }

  input {
    width: 70%;
    height: 45px;
    padding: 10px;
    margin-bottom: 25px;
    background-color: #1f2833;
    border: 2px solid #66fcf1;
    color: #66fcf1;
    font-size: 1.2rem;
    font-weight: 500;
    border-radius: 10px;
  }

  select {
    width: 70%;
    height: 45px;
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
    margin-top: 30px;
    width: 50%;
    background-color: #000;
    color: white;
    padding: 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-weight: 500;
  }
  button:hover {
    /* border: 2px solid #0b0c10; */
    color: #66fcf1;
    background-color: #1f2833;
  }

  /* add income div  */
  .addInc_div {
    width: 20%;
    height: 440px;
    font-size: 1.2rem;
    font-weight: bold;
    color: #66fcf1;
  }

  #addIncomeAuto {
    margin-top: 30px;
    background-color: #66fcf1;
  }

  /* reccent div */
  .recent_div {
    width: 30%;
    height: 700px;
    color: #66fcf1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .recent_div h1 {
    font-size: 3.5rem;
    font-weight: bolder;
    margin-top: 20px;
  }
  .recent_div ul {
    list-style-type: none;
    padding: 0;
    font-size: 1.4rem;
    margin-top: 80px;
    width: 80%;
    border-radius: 10px;
    align-items: center;
    background-color: #66fcf1;
    color: #0b0c10;
    margin-bottom: 5px;
  }
  .recent_div li p {
    font-size: 1.2rem;
    font-weight: 500;
  }

  /* Add additional styles as needed for responsiveness and aesthetics */
</style>
