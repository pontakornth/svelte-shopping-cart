<script lang="ts">
	import type Item from "../types/ShopItem"
	export let item: Item
	export let amount: number
	$: totalPrice = item.price * amount
</script>

<div class="cart-item">
	<p class="cart-item-name">{item.name}</p>
	<p class="cart-item-price">{item.price}</p>
	<p class="cart-item-amount">{amount}</p>
	<p class="cart-item-total-price">{totalPrice}</p>
</div>