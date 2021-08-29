<script>
  export let books;

  $: total = books.reduce((acc, cur) => {
    return (acc += cur.price);
  }, 0);
</script>

<h2>🛒Cart</h2>
<ul>
  {#each books as book}
    <li>{book.title} - {book.price}</li>
  {/each}
</ul>

<div class="price">Total Price: {total}</div>

<style>
  ul {
    list-style: none;
    margin: 1rem;
    padding: 0;
  }

  li {
    font-size: 1.5rem;
    margin: 1rem;
  }

  .price {
    border-top: 1px dashed black;
    padding-top: 1rem;
  }
</style>
