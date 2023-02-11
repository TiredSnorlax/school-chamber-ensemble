<script>
  import ImageContainer from "../ImageContainer.svelte";
  import Page from "../Page.svelte";
</script>

<div class="page">
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
    margin-top: 20rem;

    padding: 10rem 0;
  }
  .mediaContainer {
    padding-top: 10rem;
    display: grid;
    grid-template-columns: 1fr 1fr;
  }
</style>
