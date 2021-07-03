<script lang="ts">
	import type ShopItem from "../types/ShopItem"
	export const item: ShopItem = {id: '', name: '', price: 0}
</script>

<div class="shop-item">
	<p class="name">{item.name}</p>
	<p class="price">{item.price}</p>
	<butto class="add-button">Add to cart</butto>
</div>
