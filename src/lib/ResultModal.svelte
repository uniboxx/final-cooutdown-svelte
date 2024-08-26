<script>
  let { result, targetTime, timeRemaining, handleReset } = $props();

  const userLost = $derived(timeRemaining <= 0);
  let formattedTimeRemaining = $derived((timeRemaining / 1000).toFixed(2));
  const score = $derived(
    Math.round((1 - timeRemaining / 1000 / targetTime) * 100)
  );

  let dialog = $state();
  export function open() {
    dialog.showModal();
  }
</script>

<dialog bind:this={dialog} class="result-modal" onClose={handleReset}>
  {#if userLost}
    <h2>You lost</h2>
  {:else}
    <h2>Your score: {score}</h2>
  {/if}
  <p>
    The target time was <strong>{targetTime} seconds.</strong>
  </p>
  <p>
    You stopped the timer with <strong
      >{formattedTimeRemaining} seconds left.</strong>
  </p>
  <form method="dialog" onsubmit={handleReset}>
    <button>Close</button>
  </form>
</dialog>
