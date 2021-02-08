<template>
	<div class="home">
		<ProductListing v-on:addToCart="AddProductToCart"/>
	</div>
</template>

<script>
	// @ is an alias to /src
	import ProductListing from '@/components/ProductListing.vue'

	export default {
		name: 'Home',
		components: {
			ProductListing
		},
		methods: {
			AddProductToCart(product) {
				this.$emit('addToCart', product);
			}
		}
	}
</script>
