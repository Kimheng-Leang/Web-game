<template>
<div class="auth">
	<div class="welcome container-unique">
		<div v-if='showLogin'>
			<div class="auth-header">
				<img class="logo" src="../assets/images/Anachak_logo.svg" alt="">
				<h4>WELCOME TO ANACHAK GAME</h4>
			</div>
			<signin-form @login="enterUserpage"/>
			<p>Don't have an account? <u><span class="link-auth" @click="showLogin = false"> Sign up </span></u></p>
		</div>
		<div v-else>
			<div class="auth-header">
				<img class="logo" src="../assets/images/Anachak_logo.svg" alt="">
				<h4>BE PART OF ANACHAK GAME</h4>
			</div>
			<signup-form @signup="showLogin = true"/>
			<p>Already have an account? <u> <span class="link-auth" @click="showLogin = true"> Sign in  </span></u></p>
		</div>
	</div>
</div>
</template>

<script>
import SignupForm from '../components/SignupForm.vue'
import SigninForm from '../components/SigninForm.vue'
import { ref } from 'vue'
import { useRouter } from 'vue-router'
export default {
	components:{
		SignupForm,
		SigninForm,
	}
	,setup() {
		const showLogin = ref(true);

		const router = useRouter();

		const enterUserpage = () => {
			router.push({name : 'userpage'})
		};

		return {showLogin, enterUserpage}	
	},
}
</script>

<style>
	.welcome{
		text-align: center;
		padding: 20px 0;
	}
	.welcome form{
		width: 300px;
		margin: 20px auto;	
	}
	.welcome label{
		display: flex;
		align-content: left;
	}
	.welcome input{
		width: 95%;
		padding: 10px;
		border-radius: 20px;
		border: 1px solid #eee;
		color: black;
		outline: none;
		margin: 10px auto;
	}
	.auth-header{
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.auth-header .logo{
		margin-right: 0.5rem;
		width: 2rem;
	}
	
</style>