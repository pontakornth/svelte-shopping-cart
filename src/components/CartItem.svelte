<script lang="ts">
	import type Item from "../types/ShopItem"
	export let item: Item
	export let amount: number
	$: totalPrice = item.price * amount
</script>

<div class="cart-item">
	<p class="cart-item-description">{item.name}: {item.price}</p>
	<p class="cart-item-amount">Amount: {amount}</p>
	<p class="cart-item-total-price">Total Price: {totalPrice}</p>
</div>

<style lang="scss">
.cart-item {
	border: 1px solid black;
	padding: 1rem;
	text-align: right;
	&:not(:last-child) {
		margin-bottom: 1rem;
	}
	&-description {
		font-weight: bold;
	}
}
</style>