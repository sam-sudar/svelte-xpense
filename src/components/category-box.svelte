<script>
  export let catName, catLimit;
</script>

<div class="cat_div">
  <p id="amount_p">₹{catLimit}</p>
  <p id="cate_p">{catName}</p>
</div>

<style>
  .cat_div {
    height: 140px;
    width: 160px;
    border-radius: 25px;
    margin-left: 10px;
    background-color: #fff;
  }
  p {
    margin: 10px;
  }
  #amount_p {
    font-size: 2.4rem;
    font-weight: bold;
    margin-top: 15px;
  }
  #cate_p {
    font-size: 1.5rem;
  }
</style>
