<template>
	<div class="container mb-4">
		<div class="row">
			<div class="col-12">
				<div class="table-responsive">
					<table class="table table-striped">
						<thead>
							<tr>
								<th scope="col"> </th>
								<th scope="col">Product</th>
								<th scope="col">Available</th>
								<th scope="col" class="text-center">Quantity</th>
								<th scope="col" class="text-right">Price</th>
								<th> </th>
							</tr>
						</thead>
						<tbody>
							<tr v-for="product in cartItems" :key="product.productCode">
								<CartItem :product="product" @qtyChanged="updateTotal" />
							</tr>
							<tr>
								<td></td>
								<td></td>
								<td></td>
								<td></td>
								<td><strong>Total</strong></td>
								<td class="text-right currency"><strong>{{total}}</strong></td>
							</tr>
						</tbody>
					</table>
				</div>
			</div>
			<div class="col mb-2">
				<div class="row">
					<div class="col-sm-12 text-end">
						<router-link to="/home" class="btn btn-block btn-outline-secondary me-2">Continue Shopping</router-link>
						<button class="btn btn-block btn-outline-success text-uppercase">Checkout</button>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>


<script>
	import CartItem from '../components/CartItem.vue'
	export default {
		name: 'ShoppingCart',
		components: {
			CartItem
		},
		props: ['cartItems'],
		data() {
			return {
				total: 0,
			}
		},
		created() {
			this.updateTotal(1)
		},
		methods: {
			updateTotal(productInputQty, productInCart) {
				if (productInCart) {
					productInCart.calcPrice = parseInt(productInCart.price) * parseInt(productInputQty);
					productInCart.productInputQty = productInputQty
				}
				var sum = 0;
				for (var i = 0; i < this.cartItems.length; i++) {
					if (this.cartItems[i].calcPrice)
						sum += parseInt(this.cartItems[i].calcPrice);
					else
						sum += parseInt(this.cartItems[i].price);

				}
				this.total = sum;
			}
		}
	}
</script>