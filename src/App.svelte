<script>
  import SideBar from "./components/sidebar.svelte";
  import ExpenseForm from "./pages/expense-form.svelte";
  import Home from "./pages/home.svelte";
  import IncomeForm from "./pages/income-form.svelte";
  import CategoryForm from "./pages/category-form.svelte";

  //Store
  import { writable } from "svelte/store";

  const sharedState = writable({ message: [] });
  const newsharedState = writable({
    categoryMessage: [
      { name: "Food", maxBudget: 5000 },
      { name: "Rent", maxBudget: 6000 },
    ],
  });
  const expenseSharedState = writable({ expenseMessage: [] });

  let incomeAmount;

  function handleCustomEvent(event) {
    incomeAmount = event.detail.message;
  }
</script>

<div class="app">
  <SideBar />
  <Home {expenseSharedState} {newsharedState} {sharedState} />
  <CategoryForm {newsharedState} />
  <IncomeForm on:incomeAmountData={handleCustomEvent} {sharedState} />
  <ExpenseForm {newsharedState} {expenseSharedState} />
</div>

<style>
  .app {
    display: flex;
    flex-direction: column;
    text-align: center;
    padding: 0;
    margin: 0;
    width: 100%;
    height: 100%;
    background-color: #0b0c10;
  }

  @media (min-width: 640px) {
    .app {
      max-width: none;
    }
  }
</style>
