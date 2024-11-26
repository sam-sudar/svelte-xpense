<script>
  // import IncomeForm from "../Income_Page/IncomeForm.svelte";

  // import ExpenseForm from "../Expense_Page/ExpenseForm.svelte";
</script>

<div class="sidebar">
  <div class="sidebar-header">
    <h3>Xpense LOGO</h3>
  </div>

  <ul>
    <li><a href="#home">Home</a></li>
    <li><a href="#category">Category</a></li>
    <li><a href="#income">Income</a></li>
    <li><a href="#expense">Expenses</a></li>
  </ul>
</div>

<style>
  .sidebar {
    width: 250px;
    height: 100%;
    background-color: #0b0c10;
    position: fixed;
    top: 0;
    left: 0;
  }

  .sidebar-header {
    display: flex;
    align-items: center;
    height: 100px;
    padding: 10px;
    text-align: center;
    background-color: #0b0c10;
    margin-bottom: 20px;
  }

  ul {
    list-style-type: none;
    padding: 0;
    font-size: 1.4rem;
    margin-top: 80px;
  }

  li {
    padding: 10px;
    margin-bottom: 40px;
    color: #66fcf1;
  }

  li:hover {
    background-color: #66fcf1;
    border: 2px solid snow;
    border-radius: 40px;
  }

  a {
    text-decoration: none;
    color: #66fcf1;
  }
  li:hover a {
    font-weight: bold;
    color: #0b0c10;
  }
</style>
