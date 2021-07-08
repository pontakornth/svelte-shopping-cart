<script lang="ts">
  import ShopItem from "./components/ShopItem.svelte"
  import CartItem from "./components/CartItem.svelte"
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
    },
    {
      id: "streirtkdi",
      name: "Ghost City V",
      price: 2525
    },
    {
      id: "rsinirsndridki",
      name: "GVS",
      price: 2666
    }
  ]
  let searchTerm = ""
  let cart: Map<Item, number> = new Map()

  $: totalPrice = Array.from(cart.entries()).reduce((prev, [item, amount]) => prev + item.price*amount, 0)
  
  function addToCart(item: Item) {
    console.log(item)
    if (cart.has(item)) {
      cart.set(item, cart.get(item) + 1)
      cart = cart
    } else {
      cart.set(item, 1)
      cart = cart
    }
  }

  function handleAdd(event: CustomEvent<Item>) {
    addToCart(event.detail)
  }
</script>

<main class="main">
  <input type="text" class="search-bar" bind:value={searchTerm} />
  <div class="items-display">
    <ul class="items-list">
      {#each items as item (item.id)}
      <ShopItem {item} on:add={handleAdd} />
      {/each}
    </ul>
  </div>
  <div class="cart">
      {#each [...cart] as [item, amount] (item.id)}
        <CartItem {item} {amount} />
      {/each}
      {#if cart}
      <div class="total">
        <p>Total: {totalPrice}</p>
      </div>
      {/if}
  </div>
</main>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=K2D:ital@0;1&family=Kanit:ital,wght@0,400;0,700;1,400;1,700&display=swap');
@import "./assets/style.scss";
  :global {
    @import "normalize.css/normalize.css";
    * {
      box-sizing: border-box;
    }
    html, body {
      font-family: "K2D", sans-serif;
    }
  }
  .main {
    display: grid;
    grid-template-areas:
    "search search search" 
    "content content cart" 
    "content content cart";
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto;
    grid-gap: 10px;
    width: 80%;
    max-width: 1280px;
    margin: 2rem auto;
    border: 1px solid black;
    padding: 1.5rem;
    @extend %card-border;
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
  
  .cart {
    grid-area: cart;
    padding: 1rem;
    border: 1px solid black;
  }

  .total {
    @extend %card-border;
    text-align: right;
    padding: 1rem;
  }

</style>
