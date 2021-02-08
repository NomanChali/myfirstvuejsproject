<template>
	<header>
		<nav class="navbar navbar-expand-md navbar-dark bg-dark" v-if="isUserLoggedIn">
			<div class="container">
				<router-link to="/home" class="navbar-brand">Home</router-link>
				<button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarCollapse" aria-controls="navbarCollapse" aria-expanded="false" aria-label="Toggle navigation">
					<span class="navbar-toggler-icon"></span>
				</button>
				<div class="collapse navbar-collapse" id="navbarCollapse">
					<ul class="navbar-nav mb-2 mb-md-0 ms-auto">
						<li class="nav-item">
							<CartButton v-bind:cartCount="cartCount"  />
						</li>
					</ul>
				</div>
			</div>
		</nav>
	</header>
	<router-view v-on:setUserLoggedIn="setUserLoggedIn" v-on:addToCart="addToCart" v-bind:cartItems="cartItems" />
</template>

<script>
	import CartButton from './components/CartButtonComponent.vue'

	export default {
		name: 'App',
		components: {
			CartButton
		},
		data() {
			return {
				isUserLoggedIn: false,
				cartCount: 0,
				cartItems: [],
			}
		},
		mounted() {
			if (localStorage.isauthorize) {
				this.isUserLoggedIn = localStorage.isauthorize;
			}
		},
		methods: {
			setUserLoggedIn() {
				this.isUserLoggedIn = true;
			},
			addToCart(product) {
				this.cartItems.push(product);
				this.cartCount++;
			}
		}
	}
</script>
<style>
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
	}
	.currency::after{
		content:'$';
	}

	#nav {
		padding: 30px;
	}

		#nav a {
			font-weight: bold;
			color: #2c3e50;
		}

			#nav a.router-link-exact-active {
				color: #42b983;
			}
</style>
