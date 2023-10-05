<script>
  let incomeAmount = 0;
  let incomeSource = "";
  let incomeDate = "";
  let incomeFrequency = "";
  let isTicked = false;
  let nextIncomeDate = null;

  const incomeFrequencyOptions = ["Weekly", "Monthly", "Yearly"];
  let incomes = [];

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

    if (incomeAmount && incomeSource && incomeDate) {
      incomes = [
        {
          amount: incomeAmount,
          source: incomeSource,
          date: incomeDate,
        },
        ...incomes,
      ];

      incomeAmount = 0;
      incomeSource = "";
      incomeDate = "";
      incomeFrequency = "";
      isTicked = false;

      calculateNextIncomeDate();
    }
  }
</script>

<form on:submit={handleFormSubmit}>
  <label for="amount">Income Amount:</label>
  <input
    type="number"
    id="amount"
    placeholder="Enter the income amount"
    bind:value={incomeAmount}
  />

  <label for="income-frequency">Income Frequency:</label>
  <select
    id="income-frequency"
    bind:value={incomeFrequency}
    on:change={handleIncomeEvent}
  >
    {#each incomeFrequencyOptions as option}
      <option value={option}>{option}</option>
    {/each}
  </select>

  <label for="add-income-automatically">Add Income Automatically:</label>
  <input
    type="checkbox"
    id="add-income-automatically"
    bind:checked={isTicked}
    on:change={calculateNextIncomeDate}
  />

  <p>
    Next Income Date: {nextIncomeDate ? nextIncomeDate.toDateString() : "N/A"}
  </p>

  <label for="source">Source:</label>
  <input
    type="text"
    id="source"
    placeholder="Income source"
    bind:value={incomeSource}
  />

  <label for="date">Income Date:</label>
  <input type="date" id="date" bind:value={incomeDate} />

  <button type="submit">Add Income</button>

  {#if incomes.length > 0}
    <h2>Recent Incomes</h2>
    <ul>
      {#each incomes as income}
        <li>
          Amount: ${income.amount}, Source: {income.source}, Date: {income.date}
        </li>
      {/each}
    </ul>
  {/if}
</form>

<style>
  form {
    display: flex;
    flex-direction: column;
    max-width: 300px;
    margin: 0 auto;
  }

  label {
    font-weight: bold;
    margin-bottom: 5px;
  }

  input {
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }

  button {
    background-color: #007bff;
    color: white;
    padding: 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  /* Add additional styles as needed for responsiveness and aesthetics */
</style>
