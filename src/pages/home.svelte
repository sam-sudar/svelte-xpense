<script>
  import Endbar from "../components/endbar.svelte";
  import Mainbar from "./mainbar.svelte";

  export let sharedState;
  export let newsharedState;
  export let expenseSharedState;

  $: message = $sharedState.message;
  $: categoryMessage = $newsharedState.categoryMessage;
  $: expenseMessage = $expenseSharedState.expenseMessage;
</script>

<div class="home_div">
  <Mainbar {expenseMessage} {categoryMessage} {message} />
  <Endbar />
</div>

<style>
  .home_div {
    display: flex;
    text-align: center;
    padding: 0;
    margin: 0;
    width: 100%;
    height: 100%;
    margin-bottom: 40px;
  }
</style>
