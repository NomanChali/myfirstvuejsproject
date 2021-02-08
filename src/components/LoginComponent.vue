<template>
	<div class="text-center">
		<div class="form-signin">
			<form @submit="loginUser">
				<h1 class="h3 mb-3 fw-normal">Please sign in</h1>
				<label for="inputEmail" class="visually-hidden">Email address</label>
				<input type="email" id="inputEmail" class="form-control mb-2" v-model="user.username" placeholder="Email address" required="" autofocus="">
				<label for="inputPassword" class="visually-hidden">Password</label>
				<input type="password" id="inputPassword" class="form-control" v-model="user.password" placeholder="Password" required="">
				<button class="w-100 mt-2 btn btn-primary" type="submit">Sign in</button>
			</form>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'LoginComponent',
		data() {
			return {
				user: {
					username: '',
					password: ''
				}
			}
		},
		methods: {
			loginUser() {
				this.$emit('loginUser', this.user);
			}
		}
	}
</script>

<style scoped>
	.form-signin {
		width: 100%;
		max-width: 330px;
		padding: 15px;
		margin: auto;
		margin-top:60px
	}
</style>

