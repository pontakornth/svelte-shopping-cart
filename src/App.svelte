<script lang="ts">
  import ShopItem from "./components/ShopItem.svelte"
  import type Item from "./types/ShopItem"
  let items: Item[] = [
    {
      id: "rsitbkrseitk",
      name: "Todoroki Chocolate",
      price: 20
    },
    {
      id: "riwkdyw3kdy",
      name: "Deku Breaker",
      price: 340
    }
  ]
  let searchTerm = ""
</script>

<main class="main">
  <input type="text" class="search-bar" bind:value={searchTerm} />
  <div class="items-display">
    <ul class="items-list">
      {#each items as item (item.id)}
      <ShopItem {item} />
      {/each}
    </ul>
  </div>
  <div class="cart">
    No items in the cart
  </div>
</main>

<style lang="scss">

  :global {
    @import "normalize.css/normalize.css";
    * {
      box-sizing: border-box;
    }
  }
  .main {
    display: grid;
    grid-template-areas:
    "search search search" 
    "content content sidebar" ;
    grid-gap: 10px;
    width: 80%;
    max-width: 1280px;
    margin: 2rem auto;
    border: 1px solid black;
    padding: 1.5rem;
  }
  .search-bar {
    grid-area: search;
    padding: .85em;
  }

  .items-display {
    grid-area: content;
  }

  .items-list {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 5px;
    padding: 0;
    margin: 0;
  }

</style>
