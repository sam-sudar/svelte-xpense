<script>
  import Endbar from "./components/endbar.svelte";
  import MainBar from "./pages/mainbar.svelte";
  import SideBar from "./components/sidebar.svelte";
</script>

<div class="app">
  <SideBar />
  <MainBar />
  <Endbar />
</div>

<style>
  .app {
    display: flex;
    text-align: center;
    padding: 0;
    margin: 0;
    width: 100%;
    height: 100%;
  }

  @media (min-width: 640px) {
    .app {
      max-width: none;
    }
  }
</style>
