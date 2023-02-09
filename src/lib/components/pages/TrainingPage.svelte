<script lang="ts">
  import { fly, scale } from "svelte/transition";
  import Page from "../Page.svelte";

  export let scroll: number;
  export let pageHeight: number;

  let offset = pageHeight * 3.5;
</script>

<Page>
  {#if scroll > offset}
    <div class="popup" transition:scale>
      <p>
        Every Wednesday morning, from 7.45 to 10.45am, a handful of individuals
        convene at the Indoor Sports Hall for CCA. However, they do not belong
        to a sports CCA: the only exercise they get is carrying their
        instruments to school and playing them during CCA. What kind of bizarre,
        eccentric CCA is this? This is, of course, Chamber Ensemble! Our CCA is
        housed in the humble (and perhaps small) Chamber Room located in a
        corner of the ISH. Despite its modest size, the Chamber Room is home to
        the memories of generations of musicians. Our conductor, Mr Lin, was
        also once a starry-eyed student at the Chamber Ensemble.
      </p>
    </div>
  {/if}
</Page>

<style>
  .popup {
    margin-top: 5rem;
    height: 80vh;
    width: 90vw;

    background: rgba(255, 255, 255, 0.25);
    box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
    backdrop-filter: blur(4px);
    -webkit-backdrop-filter: blur(4px);
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.18);

    padding: 1rem;

    color: white;
    font-size: 1.2rem;
  }
</style>
