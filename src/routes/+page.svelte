<script lang="ts">
  import AudioPlayer from "$lib/components/AudioPlayer.svelte";
  import AboutPage from "$lib/components/pages/AboutPage.svelte";
  import ContactPage from "$lib/components/pages/ContactPage.svelte";
  import GalleryPage from "$lib/components/pages/GalleryPage.svelte";
  import TrainingPage from "$lib/components/pages/TrainingPage.svelte";
  import { onMount } from "svelte";
  import FirstPage from "../lib/components/pages/FirstPage.svelte";

  let scroll = 0;
  let pageHeight = 0;

  let aboutPlaceholder: HTMLDivElement;
  let trainingPlaceholder: HTMLDivElement;
  let galleryPlaceholder: HTMLDivElement;

  const onScroll = () => {
    scroll = window.scrollY;
  };

  onMount(() => {
    pageHeight = window.innerHeight;
  });
</script>

<svelte:window on:scroll={onScroll} />

<div class="page">
  <FirstPage
    {scroll}
    {pageHeight}
    {aboutPlaceholder}
    {trainingPlaceholder}
    {galleryPlaceholder}
  />
  <div bind:this={aboutPlaceholder} />
  <AboutPage {scroll} offset={pageHeight * 1.5} />
  <div bind:this={trainingPlaceholder} />
  <TrainingPage {scroll} offset={pageHeight * 3.5} />
  <div bind:this={galleryPlaceholder} />
  <GalleryPage />
  <ContactPage />

  <AudioPlayer {scroll} />
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
