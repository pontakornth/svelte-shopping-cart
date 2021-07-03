<script lang="ts">
  let searchTerm = ""
</script>

<main class="main">
  <input type="text" class="search-bar" bind:value={searchTerm} />
  <div class="items-display">
    <ul class="items-list">
      <div class="item">
        <p class="item-name">Paranormal Book</p>
        <p class="price">120 Baht</p>
        <button class="add-button">Add to cart</button>
      </div>
    </ul>
  </div>
  <div class="cart">
    No items in the cart
  </div>
</main>

<style>
  .main {
    display: grid;
    grid-template-areas:
    "search search search" 
    "content content sidebar" ;
    grid-gap: 10px;
  }
  .search-bar {
    grid-area: search;
    padding: .85em;
  }

  .items-display {
    grid-area: content;
  }

</style>