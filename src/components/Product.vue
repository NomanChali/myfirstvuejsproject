<template>
	<div class="card p-3 shadow-sm">
		<div class="p-2">
			<img v-bind:src="productUrlPrefix + product.gridViewImageUrl" class="card-img-top productImage" />
		</div>
		<div class="card-body">
			<p class="card-text">
				<a class="productUrl" v-bind:href="productUrlPrefix + product.productUrl" target="_blank">
					{{product.productName}}
				</a>
			</p>
			
			<div class="text-center currency">{{product.price}}</div>
			<div>
				<router-link to="/cart" class="btn btn-outline-success" v-if="product.isInCart" role="button">View cart</router-link>
					<button type="button" class="btn btn-outline-success" v-else v-on:click="AddProductToCart">Add to cart</button>
			</div>
		</div>
	</div>
</template>

<script>

	export default {
		name: 'ProductComponent',
		props: {
			product: Object
		},
		data() {
			return {
				productUrlPrefix: "https://www.generalmillscf.com/",
			}
		},
		methods: {
			AddProductToCart() {
				this.$emit('updateCart', this.product);
			}
		}

	}
</script>

<style scoped>
	.productImage {
		border: 1px solid #f1f1f1;
		border-radius:0;
		width: 300px;
		margin: 0 auto;
	}

	a {
		text-decoration: none;
	}
		a.productUrl:hover {
			text-decoration: underline;
		}

	.card-text {
		height: 60px;
	}

	.productUrl {
		font-size: 16px;
		font-size: 1rem;
		color: #3b3b3b;
		display: -webkit-box;
		-webkit-line-clamp: 2;
		-webkit-box-orient: vertical;
		overflow: hidden;
	}
</style>



