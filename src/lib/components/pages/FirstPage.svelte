<script lang="ts">
  import { onMount } from "svelte";
  import { fly } from "svelte/transition";

  export let scroll: number;
  export let pageHeight: number;
  export let aboutPlaceholder: HTMLDivElement;
  export let trainingPlaceholder: HTMLDivElement;
  export let galleryPlaceholder: HTMLDivElement;

  let firstEle: HTMLDivElement;
  let secondEle: HTMLDivElement;
  let thirdEle: HTMLDivElement;
  //
  let firstVisible = false;
  let secondVisible = false;
  let thirdVisible = false;

  let fade = false;
  //
  let showImg = false;

  const handleScroll = (scroll: number) => {
    if (!firstEle || !secondEle || !thirdEle) return;

    if (scroll > pageHeight && pageHeight > 0) {
      fade = true;
    } else {
      fade = false;
    }

    let redScroll = -scroll * 0.6;
    if (redScroll + pageHeight <= 70) {
      firstVisible = true;
      firstEle.style.top = -(pageHeight - 70) + "px";
    } else {
      firstVisible = false;
      firstEle.style.top = redScroll + "px";
    }

    if (scroll > pageHeight * 1) {
      let greenScroll = -(scroll - pageHeight * 1) * 0.4;
      if (greenScroll + pageHeight <= 70) {
        secondVisible = true;
        secondEle.style.top = -(pageHeight - 70) + "px";
      } else {
        secondVisible = false;
        secondEle.style.top = greenScroll + "px";
      }
    } else {
      secondEle.style.top = "0px";
    }

    if (scroll > pageHeight * 2) {
      let blueScroll = -(scroll - pageHeight * 2) * 0.3;
      if (blueScroll + pageHeight <= 70) {
        thirdVisible = true;
        thirdEle.style.top = -(pageHeight - 70) + "px";
      } else {
        thirdVisible = false;
        thirdEle.style.top = blueScroll + "px";
      }
    } else {
      thirdEle.style.top = "0px";
    }
  };

  $: {
    handleScroll(scroll);
  }

  const scrollToSection = (placeholder: HTMLDivElement) => {
    placeholder.scrollIntoView({ behavior: "smooth" });
  };

  onMount(() => {
    setTimeout(() => {
      showImg = true;
    }, 1000);
  });
</script>

<div class="top" class:fade>
  <div id="red" bind:this={firstEle} class:back={firstVisible}>
    {#if showImg}
      <img
        transition:fly={{ x: window.innerHeight / 2, y: 0 }}
        class="first-img"
        src="./Violin.png"
        alt=""
      />
    {/if}
    <button
      class:show={firstVisible}
      on:click={() => scrollToSection(aboutPlaceholder)}>About</button
    >
  </div>
  <div id="green" bind:this={secondEle} class:back={secondVisible}>
    {#if showImg}
      <div
        class="logo"
        transition:fly={{ x: window.innerHeight / 2, y: 0, delay: 100 }}
      >
        <img class="second-img" src="./violin-clipart.jpg" alt="" />
        <p class="logo-text">RI Chamber Ensemble</p>
      </div>
    {/if}
    <button
      class:show={secondVisible}
      on:click={() => scrollToSection(trainingPlaceholder)}>Trainings</button
    >
  </div>
  <div id="blue" bind:this={thirdEle} class:back={thirdVisible}>
    {#if showImg}
      <img
        transition:fly={{ x: window.innerHeight / 2, y: 0, delay: 200 }}
        class="first-img"
        src="./Violin.png"
        alt=""
      />
    {/if}
    <button
      class:show={thirdVisible}
      on:click={() => scrollToSection(galleryPlaceholder)}>Gallery</button
    >
  </div>
</div>

<style>
  .top {
    height: 100vh;

    position: relative;
  }

  .top.fade > div {
    filter: brightness(75%);
    z-index: -1;
  }

  .top > div {
    height: 102vh;
    width: calc(100% / 3);
    z-index: -1;

    border-radius: 0.5rem;
    border-top-left-radius: 0;
    border-top-right-radius: 0;

    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    padding: 1rem;

    position: fixed;
    transition: filter 0.3s;
  }

  .top > div.back {
    z-index: 10;
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

  .top > div button {
    position: absolute;
    bottom: 1rem;

    color: white;
    text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000,
      1px 1px 0 #000;
    font-size: 2.5rem;
    opacity: 0;

    transition: 0.5s;
  }

  .top > div button.show {
    opacity: 1;
  }

  .first-img {
    max-width: 300px;
  }

  .second-img {
    max-width: 300px;
    border-radius: 50%;
  }

  .logo {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .logo .logo-text {
    position: relative;
    opacity: 1;

    font-size: 2rem;
    padding-top: 1rem;
    text-align: center;
  }
</style>
