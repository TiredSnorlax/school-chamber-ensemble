<script lang="ts">
  export let scroll: number;
  let playing = false;

  let audioEle: HTMLAudioElement;

  const click = () => {
    if (playing) {
      audioEle.pause();
      playing = false;
    } else {
      audioEle.play();
      playing = true;
    }
  };
</script>

<button on:click={click}>
  <img src="./music-icon.png" alt="" hidden={!playing} />
  {#if !playing}
    <span class="material-icons-outlined"> play_arrow </span>
  {/if}
  <audio bind:this={audioEle} loop hidden>
    <source src="./test-song.mp3" type="audio/mpeg" />
  </audio>
</button>

<style>
  button {
    padding: 5px;
    border-radius: 50%;

    position: fixed;
    bottom: 2rem;
    right: 2rem;

    display: flex;

    background: green;
  }
  img {
    border-radius: 50%;
    width: 50px;

    animation: rotate 3s linear infinite;
  }

  span {
    color: white;
    display: flex;

    font-size: 50px;
  }

  @keyframes rotate {
    0% {
      transform: rotate(0);
    }

    100% {
      transform: rotate(360deg);
    }
  }
</style>
