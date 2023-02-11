<script lang="ts">
  import { fade, fly, scale, slide } from "svelte/transition";

  export let scroll: number;
  export let offset: number;
</script>

<div class="section">
  {#if scroll > offset}
    <div class="popup" transition:fade>
      <img src="./placeholder.png" alt="" />
      <div>
        <p>
          Every Wednesday morning, from 7.45 to 10.45am, a handful of
          individuals convene at the Indoor Sports Hall for CCA. However, they
          do not belong to a sports CCA: the only exercise they get is carrying
          their instruments to school and playing them during CCA. What kind of
          bizarre, eccentric CCA is this? This is, of course, Chamber Ensemble!
          Our CCA is housed in the humble (and perhaps small) Chamber Room
          located in a corner of the ISH. Despite its modest size, the Chamber
          Room is home to the memories of generations of musicians. Our
          conductor, Mr Lin, was also once a starry-eyed student at the Chamber
          Ensemble.
        </p>
      </div>
    </div>
  {/if}
</div>

<style>
  .section {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;

    margin-top: 50vh;

    height: 80vh;
  }

  .popup {
    margin-top: 5rem;
    width: 90vw;

    background: rgba(255, 255, 255, 0.25);
    box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
    backdrop-filter: blur(4px);
    -webkit-backdrop-filter: blur(4px);
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.18);

    color: white;
    font-size: 1.2rem;

    display: flex;
    flex-direction: column;
    align-items: center;

    overflow: hidden;
  }

  img {
    width: 100%;
    max-height: 50vh;
    object-fit: cover;
  }

  .popup > div {
    flex: 1 1 auto;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1rem;
  }

  p {
    line-height: 1.5rem;
  }
</style>
