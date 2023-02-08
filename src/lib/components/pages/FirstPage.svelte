<script lang="ts">
  import { onMount } from "svelte";
  import { fly } from "svelte/transition";
  import Page from "../Page.svelte";

  export let scroll: number;
  export let pageHeight: number;

  let redEle: HTMLDivElement;
  let greenEle: HTMLDivElement;
  let blueEle: HTMLDivElement;

  let redVisible = false;
  let greenVisible = false;
  let blueVisible = false;

  let showImg = false;

  const handleScroll = (scroll: number) => {
    if (!redEle || !greenEle || !blueEle) return;

    let redScroll = -scroll * 0.5;
    if (redScroll + pageHeight <= 50) {
      redVisible = true;
      redEle.style.top = -(pageHeight - 50) + "px";
    } else {
      redVisible = false;
      redEle.style.top = redScroll + "px";
    }

    if (scroll > pageHeight * 1) {
      let greenScroll = -(scroll - pageHeight) * 0.5;
      if (greenScroll + pageHeight <= 60) {
        greenVisible = true;
        greenEle.style.top = -(pageHeight - 60) + "px";
      } else {
        greenVisible = false;
        greenEle.style.top = greenScroll + "px";
      }
    } else {
      greenEle.style.top = "0px";
    }

    if (scroll > pageHeight * 2) {
      let blueScroll = -(scroll - pageHeight * 2) * 0.5;
      console.log(pageHeight + blueScroll);
      if (blueScroll + pageHeight <= 70) {
        blueVisible = true;
        blueEle.style.top = -(pageHeight - 70) + "px";
      } else {
        blueVisible = false;
        blueEle.style.top = blueScroll + "px";
      }
    } else {
      blueEle.style.top = "0px";
    }
  };

  $: {
    handleScroll(scroll);
  }

  onMount(() => {
    setTimeout(() => {
      showImg = true;
    }, 1000);
  });
</script>

<Page>
  <div class="top">
    <div id="red" bind:this={redEle}>
      {#if showImg}
        <img
          transition:fly={{ x: window.innerHeight / 2, y: 0 }}
          class="first-img"
          src="./Violin.png"
          alt=""
        />
      {/if}
      <p class:show={redVisible}>About</p>
    </div>
    <div id="green" bind:this={greenEle}>
      {#if showImg}
        <img
          transition:fly={{ x: window.innerHeight / 2, y: 0, delay: 100 }}
          class="first-img"
          src="./Violin.png"
          alt=""
        />
      {/if}
      <p class:show={greenVisible}>Training</p>
    </div>
    <div id="blue" bind:this={blueEle}>
      {#if showImg}
        <img
          transition:fly={{ x: window.innerHeight / 2, y: 0, delay: 200 }}
          class="first-img"
          src="./Violin.png"
          alt=""
        />
      {/if}
      <p class:show={blueVisible}>Gallery</p>
    </div>
  </div>
</Page>

<style>
  .top {
    height: 100vh;
    z-index: -1;

    position: relative;
  }

  .top > div {
    height: 100vh;
    width: 33%;
    z-index: -1;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    padding: 1rem;

    position: fixed;
  }

  .top > div:first-child {
    background: black;
    left: 0;
  }
  .top > div:nth-child(2) {
    background: green;
    left: 0;
    right: 0;
    margin: 0 auto;
  }
  .top > div:nth-child(3) {
    background: white;
    right: 0;
  }

  .top > div p {
    position: absolute;
    bottom: 1rem;

    color: white;
    font-size: 1.5rem;
    opacity: 0;

    transition: 0.5s;
  }

  .top > div p.show {
    opacity: 1;
  }

  .first-img {
    max-width: 300px;
  }
</style>
