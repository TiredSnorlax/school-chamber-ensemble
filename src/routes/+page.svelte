<script lang="ts">
  import AboutPage from "$lib/components/pages/AboutPage.svelte";
  import { onMount } from "svelte";
  import Page from "../lib/components/Page.svelte";
  import FirstPage from "../lib/components/pages/FirstPage.svelte";

  let scroll = 0;
  let pageHeight = 0;

  const onScroll = () => {
    scroll = window.scrollY;
  };

  onMount(() => {
    pageHeight = window.innerHeight;
  });
</script>

<svelte:window on:scroll={onScroll} />

<div class="page">
  <FirstPage {scroll} { pageHeight} />
  <Page>
    <p>Page 2</p>
  </Page>
  <AboutPage {scroll} { pageHeight} />
  <Page />
  <Page />
  <Page />
  <Page />
</div>

<style>
  :global(*) {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  :global(body) {
    overflow-x: hidden;
    background: rgb(50, 50, 50);
  }
</style>
