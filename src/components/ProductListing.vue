<template>
	<div class="album py-5 bg-light">
		<div class="container">
			<div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 g-3">
				<div class="col" v-for="product in products" :key="product.productCode">
					<Product :product="product" v-on:updateCart="AddProductToCart"/>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import Product from '@/components/Product.vue'
import { products } from "../assets/products";
export default {
	name: 'ProductListingComponent',
	components: {
		Product
	},
	data() {
		return {
			products : products.products
		}
	},
	methods: {
		AddProductToCart(product) {
			product.isInCart = true;
			this.$emit('addToCart', product);
		}
	}

}
</script>



