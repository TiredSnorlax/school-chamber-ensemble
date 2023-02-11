<script lang="ts">
  import { fade, fly, scale, slide } from "svelte/transition";

  export let scroll: number;
  export let offset: number;
</script>

<div class="section">
  {#if scroll > offset}
    <div class="popup top" transition:fade>
      <div>
        <h1>Title</h1>
        Every Wednesday morning, from 7.45 to 10.45am, a handful of individuals convene
        at the Indoor Sports Hall for CCA. However, they do not belong to a sports
        CCA: the only exercise they get is carrying their instruments to school and
        playing them during CCA. What kind of bizarre, eccentric CCA is this? This
        is, of course, Chamber Ensemble! Our CCA is housed in the humble (and perhaps
        small) Chamber Room located in a corner of the ISH. Despite its modest size,
        the Chamber Room is home to the memories of generations of musicians. Our
        conductor, Mr Lin, was also once a starry-eyed student at the Chamber Ensemble.
      </div>
      <img src="./cat.png" alt="" transition:fly={{ x: window.innerHeight }} />
    </div>
  {/if}

  {#if scroll > offset + 300}
    <div class="popup bottom" transition:fade>
      <img src="./cat.png" alt="" transition:fly={{ x: -window.innerHeight }} />
      <div>
        <h1>Title 2</h1>
        Every Wednesday morning, from 7.45 to 10.45am, a handful of individuals convene
        at the Indoor Sports Hall for CCA. However, they do not belong to a sports
        CCA: the only exercise they get is carrying their instruments to school and
        playing them during CCA. What kind of bizarre, eccentric CCA is this? This
        is, of course, Chamber Ensemble! Our CCA is housed in the humble (and perhaps
        small) Chamber Room located in a corner of the ISH. Despite its modest size,
        the Chamber Room is home to the memories of generations of musicians. Our
        conductor, Mr Lin, was also once a starry-eyed student at the Chamber Ensemble.
      </div>
    </div>
  {/if}
</div>

<style>
  .section {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;

    height: 100vh;
    margin-top: 100vh;
  }

  .popup {
    margin-top: 5rem;
    height: 400px;

    padding: 1rem;

    display: grid;
    align-items: center;
    gap: 1rem;
  }

  img {
    width: 100%;
  }

  .popup div {
    background: rgba(255, 255, 255, 0.25);
    box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
    backdrop-filter: blur(4px);
    -webkit-backdrop-filter: blur(4px);
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.18);

    color: white;
    font-size: 1.2rem;

    padding: 2rem 1rem;
  }

  .popup.top {
    grid-template-columns: 6fr 4fr;
  }

  .popup.bottom {
    grid-template-columns: 4fr 6fr;
  }
</style>
