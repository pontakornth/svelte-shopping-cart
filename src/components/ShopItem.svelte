<script lang="ts">
	import type ShopItem from "../types/ShopItem"
	export let item: ShopItem = {id: '', name: '', price: 0}
</script>

<div class="shop-item">
	<p class="name">{item.name}</p>
	<p class="price">{item.price}</p>
	<button class="add-button">Add to cart</button>
</div>

<style lang="scss">
	.shop-item {
		border: 1px solid black;
		padding: 1rem;
	}
</style>