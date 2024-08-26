<script>
  import Player from './lib/Player.svelte';
  import TimerChallenge from './lib/TimerChallenge.svelte';
</script>

<Player />
<div id="challenges">
  <TimerChallenge title="Easy" targetTime={1} />
  <TimerChallenge title="Not easy" targetTime={5} />
  <TimerChallenge title="Getting tough" targetTime={10} />
  <TimerChallenge title="Pros only" targetTime={15} />
</div>

<style lang="scss">
  @use './styles/vars';
</style>
