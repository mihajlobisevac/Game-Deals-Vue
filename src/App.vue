<template>
	<Header :theme="theme" @toggle-theme="toggleTheme" />
	<main>
		<router-view/>
	</main>
	<Footer />
</template>

<script>
import Header from '@/components/Header'
import Footer from '@/components/Footer'

export default {
	name: 'App',
	components: {
		Header,
		Footer
	},
	data() {
		return {
			theme: ""
		}
	},
	mounted() {
		if(localStorage.theme) {
			this.theme = localStorage.theme
		} else {
			this.theme = this.defaultTheme
		}
	},
	methods: {
		toggleTheme() {
			this.theme === "dark" ? this.theme = "light" : this.theme = "dark"
		}
	},
	watch: {
		theme(newTheme) {
			localStorage.theme = newTheme
			document.documentElement.dataset.theme = newTheme
		}
	},
	computed: {
		defaultTheme() {
			return "light"
		}
	}
}
</script>

<style>
* {
	--border-radius: 10px;
	--box-shadow: 4px 3px 15px 0px var(--clr-silver);

	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

*[data-theme=light] {
	--clr-black: #242527;
	--clr-gray: #4a4e53;
	--clr-light__gray: #84888f;
	--clr-silver: #babec5;
	--clr-dark__white: #dce0e4;
	--clr-white: #ecf0f5;
	--clr-purple: #7a00ff;
}

*[data-theme=dark] {
	--clr-black: #242527;
	--clr-gray: #dce0e4;
	--clr-light__gray: #84888f;
	--clr-silver: #131315;
	--clr-dark__white: #2c2d2f;
	--clr-white: #242527;
	--clr-purple: #9647ff;
}

.noselect {
  -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
     -khtml-user-select: none; /* Konqueror HTML */
       -moz-user-select: none; /* Old versions of Firefox */
        -ms-user-select: none; /* Internet Explorer/Edge */
            user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome, Edge, Opera and Firefox */
}

#app {
	font-family: 'Lato', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: var(--clr-gray);
}

body {
	background: var(--clr-white);
}

main {
	padding: 0 1rem;
}

@media (min-width: 960px) {
	main {
		max-width: 960px;
		margin: 0 auto;
	}
}

a {
	text-decoration: none;
	color: inherit;
}

.purple-text {
	color: var(--clr-purple)
}

.gray-text {
	color: var(--clr-gray)
}

input {
	font-family: 'Lato', Helvetica, Arial, sans-serif;
}

@-webkit-keyframes fadeIn {
	0% {
		opacity: 0;
	}
	100% {
		opacity: 100;
	}
}

@keyframes fadeIn {
	0% {
		opacity: 0;
	}
	100% {
		opacity: 100;
	}
}

@-webkit-keyframes popOut {
	0% {
		transform: scale(0);
	}
	85% {
		transform: scale(1.4);
	}
	100% {
		transform: scale(1);
	}
}

@keyframes popOut {
	0% {
		transform: scale(0);
	}
	85% {
		transform: scale(1.4);
	}
	100% {
		transform: scale(1);
	}
}

@-webkit-keyframes slideInNav {
	0% {
		transform: translateX(100%);
	}
	100% {
		transform: translateX(0);
	}
}

@keyframes slideInNav {
	0% {
		transform: translateX(100%);
	}
	100% {
		transform: translateX(0);
	}
}

@-webkit-keyframes slideInSearch {
	0% {
		transform: translateX(-100%);
	}
	85% {
		transform: translateX(15%);
	}
	100% {
		transform: translateX(0);
	}
}

@keyframes slideInSearch {
	0% {
		transform: translateX(-100%);
	}
	85% {
		transform: translateX(15%);
	}
	100% {
		transform: translateX(0);
	}
}

</style>
