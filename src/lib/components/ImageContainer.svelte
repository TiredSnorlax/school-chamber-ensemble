<script lang="ts">
  export let path: string;
  export let description: string;

  let open = false;
</script>

<button on:click={() => (open = !open)}>
  <img src={path} alt="" />
  <span>{description}</span>
  {#if open}
    <div class="expand">
      <img src={path} alt="" />
    </div>
  {/if}
</button>

<style>
  button {
    position: relative;

    aspect-ratio: 1;
    max-width: 600px;
    overflow: hidden;

    display: flex;
    justify-content: center;
    align-items: center;
  }

  button::after {
    content: "";
    position: absolute;
    inset: 0;

    background: rgba(0, 0, 0, 0);

    transition: 0.1s;
  }

  button:hover::after {
    background: rgba(0, 0, 0, 0.3);
  }

  span {
    position: absolute;
    inset: 0;
    margin: auto;
    width: fit-content;
    height: fit-content;

    font-size: 1.5rem;

    color: white;
    opacity: 0;
    transition: 0.3s;
    z-index: 5;
  }

  button:hover span {
    opacity: 1;
  }

  img {
    height: 100%;
  }

  .expand {
    position: fixed;

    inset: 0;

    background: rgba(0, 0, 0, 0.3);

    display: flex;
    justify-content: center;
    align-items: center;

    z-index: 100;
  }

  .expand img {
    width: 100vw;
    height: auto;
  }
</style>
