<script>
  import { onMount, getContext } from "svelte";

  export let navigation;
</script>

<h3>What is a procedure?</h3>
<p>
  There are times when a set of actions must be done in "procedures". For
  instance, you might need a step-by-step form that requires a fetch call to
  validate user's input. svelte-procedures is a package that assists you through
  such design patterns.
</p>

<button on:click={navigation.next}>Next!</button>
