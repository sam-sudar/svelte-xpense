<script>
  let items = [
    { id: 1, sub: "Item 1", desc: "Place", money: 400, time: "11:00" },
    { id: 2, sub: "Item 2", desc: "Place", money: 400, time: "11:00" },
    { id: 3, sub: "Item 3", desc: "Place", money: 400, time: "11:00" },
    { id: 4, sub: "Item 4", desc: "Place", money: 400, time: "11:00" },
    { id: 5, sub: "Item 5", desc: "Place", money: 400, time: "11:00" },
    { id: 6, sub: "Item 6", desc: "Place", money: 400, time: "11:00" },
    { id: 7, sub: "Item 7", desc: "Place", money: 400, time: "11:00" },
    { id: 8, sub: "Item 8", desc: "Place", money: 400, time: "11:00" },
    { id: 9, sub: "Item 9", desc: "Place", money: 400, time: "11:00" },
    { id: 10, sub: "Item 10", desc: "Place", money: 400, time: "11:00" },
  ];
</script>

<div class="scrollable-list">
  <div class="scrollable-content">
    {#each items as item (item.id)}
      <div class="item">
        <div id="itemleft_div">
          <p id="itemsub_p">{item.sub}</p>
          <p>{item.desc}</p>
        </div>
        <div id="itemright_div">
          <p style="font-weight: bold;">₹{item.money}</p>
          <p>{item.time}</p>
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
    background-color: yellow;
    text-align: left;
    padding: 0px 20px;
  }
  #itemright_div {
    width: 50%;
    height: 100%;
    background-color: lightseagreen;
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
