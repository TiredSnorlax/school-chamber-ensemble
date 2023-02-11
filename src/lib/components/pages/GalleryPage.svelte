<script>
  import ImageContainer from "../ImageContainer.svelte";
  import Page from "../Page.svelte";
</script>

<div class="page">
  <h2>Gallery</h2>
  <div class="mediaContainer">
    <ImageContainer path={"./cat.png"} description={"Test"} />
    <ImageContainer path={"./cat.png"} description={"Test"} />
    <ImageContainer path={"./cat.png"} description={"Test"} />
    <ImageContainer path={"./cat.png"} description={"Test"} />
    <ImageContainer path={"./cat.png"} description={"Test"} />
    <ImageContainer path={"./cat.png"} description={"Test"} />
  </div>
</div>

<style>
  .page {
    width: 100%;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
    margin-top: 25vh;

    padding: 10vh;
  }
  h2 {
    padding-top: 10rem;
  }
  .mediaContainer {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }

  .mediaContainer > :global(div) {
    width: 600px;
  }
</style>
