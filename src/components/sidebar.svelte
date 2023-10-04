<script>
  import { Router, Link, Route } from "svelte-routing";
  import IncomeForm from "../pages/income-form.svelte";
  import ExpenseForm from "../pages/expense-form.svelte";
</script>

<Router>
  <Route path="/income" component={IncomeForm} />

  <div class="sidebar">
    <!-- class:open={isOpen} -->
    <div class="sidebar-header">
      <h3>Expense Manager</h3>
    </div>

    <Link to="/">Home</Link>
    <Link to="/income">About</Link>
    <Link to="/expense">Blog</Link>
    <ul>
      <li><a href="/categories">Expenses</a></li>
      <li><a href="../Income_Page/IncomeForm.svelte">Income</a></li>
    </ul>
    <div>
      <Route path="/expense" component={ExpenseForm} />
      <Route path="/income" component={IncomeForm} />
    </div>
  </div>
</Router>

<style>
  .sidebar {
    width: 250px;
    height: 100%;
    background-color: red;
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
