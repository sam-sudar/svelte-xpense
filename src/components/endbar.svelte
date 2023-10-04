<script>
  let amount = 3000;
  let spent = 400;
</script>

<div class="endbar_div">
  <div class="daily_div">
    <p id="amount_p">₹{amount}</p>
    <p id="text_p">DAILY BUDGET</p>
    <div class="v_div">
      <div class="vbox_div">
        <p>Spent</p>
        <p id="vamount_p">₹{spent}</p>
      </div>
      <div class="vbox_div">
        <p>Left</p>
        <p id="vamount_p">₹{amount - spent}</p>
      </div>
    </div>
  </div>
  <div class="goals_div">
    <p>Overview</p>
  </div>
</div>

<style>
  .endbar_div {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 15px;
    background-color: black;
    height: 100%;
    width: 28%;
  }
  /* Daily budget */

  .daily_div {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 90%;
    height: 45%;
    background-color: #fff;
    margin: 15px 0px 15px;
    border-radius: 23px;
    padding-top: 15px;
  }
  .v_div {
    display: flex;
    width: 90%;
    height: 47%;
    background-color: crimson;
    align-items: center;
    justify-content: center;
  }
  .vbox_div {
    height: 89%;
    width: 44%;
    margin: 5px;
    background-color: chartreuse;
  }
  p {
    margin: 8px 0;
    font-size: 1.8rem;
  }
  #vamount_p {
    font-size: 2.3rem;
    font-weight: bold;
  }

  /* Goals */
  .goals_div {
    width: 90%;
    height: 45%;
    background-color: #fff;
    margin-top: 15px;
    border-radius: 23px;
  }
  #amount_p {
    font-size: 2.3rem;
    font-weight: bolder;
    margin: 0;
  }
  .goals_div p {
    margin: 10px 0;
    font-size: 1.6rem;
    font-weight: 500;
  }
</style>
