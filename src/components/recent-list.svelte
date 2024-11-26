<script>
  export let expenseMessage;
  const currentDate = new Date().getDate();
  const month = new Date().getMonth() + 1;
  // let items = [
  //   {
  //     id: 1,
  //     sub: "Item 1",
  //     desc: expenseMessage.expName,
  //     money: expenseMessage.expAmount,
  //     time: currentDate.getUTCDate(),
  //   },
  // ];
</script>

<div class="scrollable-list">
  <div class="scrollable-content">
    {#each expenseMessage as expense}
      <div class="item">
        <div id="itemleft_div">
          <p id="itemsub_p">{expense.name}</p>
          <p>{expense.category}</p>
        </div>
        <div id="itemright_div">
          <p style="font-weight: bold;">₹{expense.amount}</p>
          <p>{currentDate}-{month}</p>
        </div>
      </div>
    {/each}
  </div>
</div>

<style>
  .scrollable-list {
    width: 100%;
    height: 220px;
    overflow: auto;
  }

  .scrollable-content {
    width: 100%;
    display: flex;
    flex-direction: column;
  }

  /* Item  */

  .item {
    display: flex;
    height: 55px;
    border: 1px solid #ccc;
    position: relative;
  }
  #itemleft_div {
    width: 50%;
    height: 100%;
    background-color: #66fcf1;
    color: #0b0c10;
    text-align: left;
    padding: 0px 20px;
  }
  #itemright_div {
    width: 50%;
    height: 100%;
    background-color: #0b0c10;
    color: #66fcf1;
    text-align: right;
    padding: 0px 20px;
  }

  #itemsub_p {
    font-weight: 700;
  }
  .item p {
    margin: 0;
    display: block;
    left: 0;
    font-size: 1.2rem;
  }

  .scrollable-list::-webkit-scrollbar {
    width: 0.5em;
  }

  .scrollable-list::-webkit-scrollbar-thumb {
    background-color: transparent;
  }
</style>
