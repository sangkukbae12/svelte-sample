<script>
  import { createEventDispatcher } from "svelte";
  import Button from "./button.svelte";
  export let bookTitle;
  export let bookPrice;
  export let bookDescription;

  const dispatch = createEventDispatcher();

  function purchaseBook() {
    dispatch("buy", bookTitle);
  }
</script>

<div>
  <h2>{bookTitle}</h2>
  <p>{bookPrice}</p>
  <p>{bookDescription}</p>
  <Button on:click={purchaseBook}>Buy</Button>
</div>

<style>
  div {
    margin: 1rem;
    padding: 1em;
    border-radius: 4px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  }
</style>
