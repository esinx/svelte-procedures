<script>
  import { createEventDispatcher } from "svelte";
  import { writable } from "svelte/store";

  import Progress from "./Progress.svelte";

  export let procedures = [];
  export let currentStepIndex = 0;
  export let loop = false;
  export let datastore = writable({});

  export let displayProgress = true;

  const dispatch = createEventDispatcher();

  const navigation = {
    to: index => {
      currentStepIndex = index;
    },
    currentIndex: () => currentStepIndex,
    previous: props => {
      currentStepIndex = (currentStepIndex - 1) % procedures.length;
    },
    hasPrevious: () => currentStepIndex - 1 > -1,
    next: props => {
      if (loop) {
        currentStepIndex = (currentStepIndex + 1) % procedures.length;
      } else {
        if (currentStepIndex + 1 < procedures.length) {
          currentStepIndex = currentStepIndex + 1;
        } else {
          dispatch("complete", $datastore);
        }
      }
    },
    hasNext: () => currentStepIndex + 1 < procedures.length
  };
</script>

{#if displayProgress}
  <slot name="progress" {procedures} {currentStepIndex}>
    <Progress {procedures} {currentStepIndex} />
  </slot>
{/if}
{#if procedures[currentStepIndex]}
  {#if procedures[currentStepIndex].props}
    <svelte:component
      this={procedures[currentStepIndex].component}
      {...procedures[currentStepIndex].props}
      {datastore}
      {navigation} />
  {:else}
    <svelte:component
      this={procedures[currentStepIndex].component}
      {datastore}
      {navigation} />
  {/if}
{/if}
