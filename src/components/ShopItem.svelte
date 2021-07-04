<script lang="ts">
import { createEventDispatcher } from "svelte";

	import type ShopItem from "../types/ShopItem"
	export let item: ShopItem = {id: '', name: '', price: 0}
	const dispatch = createEventDispatcher()
	function addToCart() {
		dispatch('add', item)
	}
</script>

<div class="shop-item">
	<p class="name">{item.name}</p>
	<p class="price">{item.price}</p>
	<button class="add-button" on:click={addToCart}>Add to cart</button>
</div>

<style lang="scss">
	.shop-item {
		border: 1px solid black;
		padding: 1rem;
	}
</style>