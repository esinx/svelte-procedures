<script>
  import Procedures from "svelte-procedures";

  import Introduction from "./procedures/introduction.svelte";
  import Introduction2 from "./procedures/introduction-2.svelte";
  import ViewText from "./procedures/view-text.svelte";

  const procedures = [
    {
      name: "Introduction",
      component: Introduction
    },
    {
      name: "Introduction 2",
      component: Introduction2
    },
    {
      name: "View Text Data",
      component: ViewText
    }
  ];
</script>

<style>
  .root {
    width: 100vw;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .root .centerbox {
    margin: auto;
    width: 90vw;
    max-width: 800px;
    padding: 40px 20px;
    border: solid #ccc 1px;
    border-radius: 10px;
  }
</style>

<div class="root">
  <div class="centerbox">
    <h1>Svelte Procedures</h1>
    <Procedures {procedures} />
  </div>
</div>
