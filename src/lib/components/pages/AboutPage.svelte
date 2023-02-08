<script lang="ts">
  import { fly, scale } from "svelte/transition";
  import Page from "../Page.svelte";

  export let scroll: number;
  export let pageHeight: number;
</script>

<Page>
  {#if scroll > pageHeight}
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
    background: white;
    border: 1px solid black;
    margin-top: 5rem;
    height: 60vh;
    width: 80vw;
  }
</style>
