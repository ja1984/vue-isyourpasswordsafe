<template>
	<div id="app">
		<GitHubLogo />
		<h2>Create an account demo</h2>
		<input type="text" placeholder="Your username">
		<vue-isyourpasswordsafe v-model="myStrongPassword"
			placeholder="Your password"
			@onFinishedChecking="isPasswordSafe"/>
		<input type="password" placeholder="Retype your password">
		<input type="email" placeholder="Your email">

		<h4 v-if="isSafe">Your password should be good to go :)</h4>
		<h4 v-if="isSafe === false"
			class="error">Your password has been leaked and you <b>shouldn't</b> use it!</h4>
	</div>
</template>
<script>
import GitHubLogo from './GithubLogo';
export default {
	components: {
		GitHubLogo
	},
	data() {
		return {
			myStrongPassword: null,
			isSafe: null
		};
	},
	methods: {
		isPasswordSafe(val) {
			this.isSafe = val;
		}
	}
};
</script>
<style>
	@import url('https://fonts.googleapis.com/css?family=Nunito');
	* {
		font-family: 'Nunito', sans-serif;
		font-weight: 300;
	}
	body {
		margin: 0px;
	}
	div#app {
		background: #f5f6f8;
		height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
	}

	div#app input {
		-webkit-box-align: center;
		-ms-flex-align: center;
		align-items: center;
		display: -webkit-inline-box;
		display: -ms-inline-flexbox;
		display: inline-flex;
		font-size: 1rem;
		height: 2.5em;
		-webkit-box-pack: start;
		-ms-flex-pack: start;
		justify-content: flex-start;
		line-height: 1.5;
		padding-left: .75em;
		padding-right: .75em;
		background-color: #fff;
		border: 1px solid #dbdbdb;
		color: #363636;
		width: 350px;
		border-left: 0px;
		border-top: 0px;
		border-right: 0px;
		border-radius: 0px;
		box-shadow: 0 0 0;
		text-align: center;
		margin-bottom: 10px;
	}

	div#app b {
		font-weight: bold;
		text-decoration: underline;
	}

	div#app .error {
		color: #ce0505;
	}

	.github-corner:hover .octo-arm {
		animation: octocat-wave 560ms ease-in-out
	}
	@keyframes octocat-wave {
		0%,100% {
			transform: rotate(0)
		}
		20%,60% {
			transform: rotate(-25deg)
		}
		40%,80% {
			transform: rotate(10deg)
		}
	}
	@media (max-width:500px) {
		.github-corner:hover .octo-arm {
			animation: none
		}
		.github-corner .octo-arm {
			animation: octocat-wave 560ms ease-in-out
		}
	}
</style>
