<script>
  import CategoryBox from "../components/category-box.svelte";
  import RecentExpenseList from "../components/recent-list.svelte";
</script>

<div class="MainBar_div">
  <h1>Earnings</h1>
  <div id="account_div">
    <p>My Balance</p>
    <p id="amount_p">₹ 33400</p>
  </div>
  <div id="cate_div">
    <CategoryBox />
    <CategoryBox />
    <CategoryBox />
    <CategoryBox />
    <CategoryBox />
  </div>
  <h1 id="rec_h1">Last Spendings</h1>
  <div id="rec_div">
    <RecentExpenseList />
  </div>
</div>

<style>
  .MainBar_div {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin-left: 250px;
    padding: 15px;
    background-color: blueviolet;
    height: 100%;
    width: 58%;
  }
  h1 {
    margin: 0;
    color: #fff;
  }

  p {
    color: #fff;
    margin: 0;
    font-size: 1.3rem;
    text-align: left;
    padding: 20px 30px 0px;
  }

  #account_div {
    height: 160px;
    width: 100%;
    background-color: #333;
    margin: 15px 0px 35px;
    border-radius: 25px;
  }
  #amount_p {
    padding: 0px 35px;
    text-align: left;
    color: #fff;
    margin: 0;
    font-size: 4.5rem;
  }

  /* Categories */
  #cate_div {
    display: flex;
    width: 100%;
    height: 150px;
  }

  /* Recent */
  #rec_h1 {
    margin: 10px 0;
  }
  #rec_div {
    width: 100%;
  }
</style>
