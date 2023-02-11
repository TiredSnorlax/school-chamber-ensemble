<script lang="ts">
  export let path: string;
  export let description: string;
</script>

<div>
  <img src={path} alt="" />
  <span>{description}</span>
</div>

<style>
  div {
    position: relative;
  }

  div::after {
    content: "";
    position: absolute;
    inset: 0;

    background: rgba(0, 0, 0, 0);

    transition: 0.3s;
  }

  div:hover::after {
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

  div:hover span {
    opacity: 1;
  }

  img {
    width: 100%;
  }
</style>
