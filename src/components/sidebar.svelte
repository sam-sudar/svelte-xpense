<script>
  // import IncomeForm from "../Income_Page/IncomeForm.svelte";

  // import ExpenseForm from "../Expense_Page/ExpenseForm.svelte";
</script>

<div class="sidebar">
  <!-- class:open={isOpen} -->
  <div class="sidebar-header">
    <h3>Expense Manager LOGO</h3>
  </div>

  <ul>
    <li>Home</li>
    <li><a href="/categories">Expenses</a></li>
    <li><a href="../Income_Page/IncomeForm.svelte">Income</a></li>
  </ul>
</div>

<style>
  .sidebar {
    width: 250px;
    height: 100%;
    background-color: #333;
    color: #fff;
    position: fixed;
    top: 0;
    left: 0;
    transition: left 0.3s ease-in-out;
  }

  .sidebar-header {
    display: flex;
    align-items: center;
    height: 100px;
    padding: 10px;
    text-align: center;
    background-color: #222;
  }

  /* ul {
    list-style-type: none;
    padding: 0;
    font-size: 1.2rem;
  }

  li {
    padding: 10px;
    margin-bottom: 20px;
  }

  a {
    text-decoration: none;
    color: #fff;
  } */
</style>
