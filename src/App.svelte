<script>
  import Book from "./components/book.svelte";
  import Button from "./components/button.svelte";
  import Purchase from "./components/purchase.svelte";

  let title = "";
  let price = 0;
  let description = "";

  let books = [];
  let purchases = [];

  function setTitle(event) {
    title = event.target.value;
  }

  function addBook() {
    const newBook = {
      title,
      price,
      description
    };
    books = books.concat(newBook);
  }

  function purchaseBook(event) {
    const selectedTitle = event.detail;
    purchases = purchases.concat({
      ...books.find(book => book.title === selectedTitle)
    });
  }
</script>

<section>
  <h1>📙Book Store</h1>
  <hr />
  <h2>Add New Book</h2>
  <div>
    <label for="title">Title</label>
    <input type="text" id="title" value={title} on:input={setTitle} />
  </div>
  <div>
    <label for="price">Price</label>
    <input type="number" id="price" bind:value={price} />
  </div>
  <div>
    <label for="description">description</label>
    <textarea row={3} id="description" bind:value={description} />
  </div>
  <Button on:click={addBook}>Add Book</Button>
</section>

<section>
  <h2>🎒️Stock</h2>
  {#if books.length === 0}
    <p>No books in stock.</p>
  {:else}
    {#each books as book}
      <Book
        bookTitle={book.title}
        bookPrice={book.price}
        bookDescription={book.description}
        on:buy={purchaseBook}
      />
    {/each}
  {/if}
</section>

<section>
  <Purchase books={purchases} />
</section>

<style>
  section {
    margin: auto;
    width: 30rem;
  }

  label,
  input,
  textarea {
    width: 100%;
    border-radius: 4px;
  }

  div > label {
    margin-top: 0.8rem;
  }

  label {
    margin-bottom: 0.3rem;
  }
</style>
