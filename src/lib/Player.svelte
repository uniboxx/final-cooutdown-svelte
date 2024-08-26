<script>
  let enteredPlayerName = $state();
  // let submitted = $state(false);
  // $inspect(submitted);
  let playerName;

  // function handleChangeName(e) {
  //   submitted = false;
  //   enteredPlayerName = e.target.value;
  // }

  function handleClick() {
    if (playerName.value) enteredPlayerName = playerName.value;
    playerName.value = '';
  }
</script>

<section id="player">
  <h2>Welcome {enteredPlayerName ?? 'unknown entity'}</h2>
  <p>
    <input bind:this={playerName} type="text" />
    <button onclick={handleClick}>Set Name</button>
  </p>
</section>
