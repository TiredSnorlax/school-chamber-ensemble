<script>
  import Page from "../Page.svelte";
</script>

<div class="page">
  <h2>Gallery</h2>
  <div class="mediaContainer">
    <img src="./cat.png" alt="" />
    <img src="./cat.png" alt="" />
    <img src="./cat.png" alt="" />
    <img src="./cat.png" alt="" />
    <img src="./cat.png" alt="" />
    <img src="./cat.png" alt="" />
    <img src="./cat.png" alt="" />
    <img src="./cat.png" alt="" />
  </div>
</div>

<style>
  .page {
    width: 100%;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
  }
  h2 {
    padding-top: 10rem;
  }
  .mediaContainer {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }

  img {
    width: 400px;
    object-fit: fill;
  }
</style>
