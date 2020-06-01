<script>
  export let datastore;
  export let navigation;

  let text = $datastore.text || "";
</script>

<h3>So what?</h3>
<p>You could possibly pass around data across procedures.</p>

<input bind:value={text} />
<button on:click={navigation.previous}>Prev!</button>
<button
  on:click={() => {
    datastore.set({ ...$datastore, text });
    navigation.next();
  }}>
  Next!
</button>
