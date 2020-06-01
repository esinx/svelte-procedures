<script>
  export let datastore;
  export let navigation;
</script>

<p>Like this: {$datastore.text}</p>

<button on:click={navigation.previous}>Prev!</button>
<button on:click={navigation.next}>Next!</button>
