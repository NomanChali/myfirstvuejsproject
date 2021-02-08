<template>
	<td><img v-bind:src="productUrlPrefix + product.gridViewImageUrl" style="width:100px" /> </td>
	<td>{{product.productName}}</td>
	<td>In stock</td>
	<td class="text-center col-sm-1">
		<input class="form-control" v-model="productInputQty" type="number" min="1" v-on:change="updateTotal" />
	</td>
	<td class="text-right "><span class="currency">{{productInputQty * product.price}}</span></td>
	<td class="text-right"><button class="btn btn-sm btn-outline-danger">&times; </button> </td>
</template>

<script>

	export default {
		name: 'CartItem',
		components: {

		},
		props: {
			product: Object
		},
		data() {
			return {
				productUrlPrefix: "https://www.generalmillscf.com/",
				productInputQty: 1
			}
		},
		created() {
			if (this.product.productInputQty)
			this.productInputQty=this.product.productInputQty
		},
		methods: {
			updateTotal() {
				this.$emit('qtyChanged', this.productInputQty, this.product)
			}
		}
	}
</script>