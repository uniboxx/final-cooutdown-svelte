<script>
  import ResultModal from './ResultModal.svelte';

  let { title, targetTime } = $props();
  // let timerStarted = $state(false);
  // let timerExpired = $state(false);
  let timeRemaining = $state(targetTime * 1000);
  let timerIsActive = $derived(
    timeRemaining > 0 && timeRemaining < targetTime * 1000
  );
  $inspect(timerIsActive);
  $inspect(timeRemaining);
  let modal;

  let timer;

  function handleReset() {
    timeRemaining = targetTime * 1000;
  }

  function handleStart() {
    // timerStarted = true;
    timer = setInterval(() => {
      //   timerExpired = true;
      //   modal.open();
      timeRemaining -= 10;
      if (timeRemaining === 0) {
        clearInterval(timer);
        modal.open();
      }
      // }, targetTime * 1000);
    }, 10);
  }

  function handleStop() {
    clearInterval(timer);
    modal.open();
  }
</script>

<ResultModal bind:this={modal} {targetTime} {timeRemaining} {handleReset} />

<section class="challenge">
  <h2>{title}</h2>
  <p class="challenge-time">
    {targetTime} second{targetTime > 1 ? 's' : ''}
  </p>
  <p>
    <button onclick={timerIsActive ? handleStop : handleStart}>
      {timerIsActive ? 'Stop' : 'Start'} Challenge
    </button>
  </p>
  <p class={timerIsActive ? 'active' : ''}>
    {timerIsActive ? 'Time is running...' : 'Timer inactive'}
  </p>
</section>
