<script>
  export let procedures;
  export let currentStepIndex;
</script>

<style>
  .progress {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
    margin: 10px 0;
    --progress-color: #fc4988;
  }
  .procedure-item {
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 10px;
    border-radius: 5px;
  }
  .procedure-item .index {
    width: 30px;
    height: 30px;
    background: #888;
    color: white;
    border-radius: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 15px;
    transition: all 0.3s;
  }
  .procedure-item.active .index {
    background: var(--progress-color);
  }
  .procedure-item .name {
    margin-left: 10px;
    font-size: 15px;
  }
</style>

<div class="progress">
  {#each procedures as procedure, i}
    <div class="procedure-item" class:active={i == currentStepIndex}>
      <div class="index">{i + 1}</div>
      <div class="name">{procedure.name}</div>
    </div>
  {/each}
</div>
