<script>
  import { writable } from "svelte/store";

  import Progress from "./Progress.svelte";

  export let procedures = [];
  export let currentStepIndex = 0;

  const datastore = writable({});

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
      currentStepIndex = (currentStepIndex + 1) % procedures.length;
    },
    hasNext: () => currentStepIndex + 1 < procedures.length
  };
</script>

<div class="procedures">
  <slot name="progress" {procedures} {currentStepIndex}>
    <Progress {procedures} {currentStepIndex} />
  </slot>
  <div class="content">
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
  </div>
</div>
