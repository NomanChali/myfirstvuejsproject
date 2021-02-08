<template>
	<LoginComponent v-on:loginUser="validateAndLoginUser" />
</template>

<script>
	import LoginComponent from '../components/LoginComponent.vue'

	export default {
		name: 'Login',
		components: {
			LoginComponent
		},
		props: {
			user: Object
		},
		data() {
			return {
			}
		},
		methods: {
			validateAndLoginUser(userCred) {
				if (!userCred)
					return;
				this.Authenticate(userCred);
			},
			Authenticate(userCred) {
				if (userCred.username == 'user@test.com' && userCred.password == 'password321')
					localStorage.isauthorize = true;
				this.redirectUser(localStorage.isauthorize);
			},
			redirectUser(isAuthenticated) {
				if (!isAuthenticated)
					return;
				this.$emit('setUserLoggedIn');
				this.$router.push('Home');
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
</style>
