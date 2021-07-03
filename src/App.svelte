<script lang="ts">
  import ShopItem from "./components/ShopItem.svelte"
  import GlobalStyle from "./components/GlobalStyle.svelte"
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

<h1>srtkrsitki</h1>
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
    @import "normalize.css/normalize.css"
  }
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

  .items-list {
    display: grid;
    grid-template-areas: repeat(3, 1fr);
    grid-gap: 5px;
  }

</style>
