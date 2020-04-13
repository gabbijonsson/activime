<template>
	<div id="app" class="spa--layout">
		<Header/>
		<FirstPage/>
		<Footer/>
	</div>
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'
import FirstPage from './components/FirstPage'

export default {
	name: 'App',
	components: {
		Header,
		Footer,
		FirstPage
	}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat&display=swap');

* {
	box-sizing: border-box;
}

body, html {
	margin: 0;
}

#app {
	font-family: 'Montserrat', sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	/* text-align: center; */
	color: #2c3e50;
	/* margin-top: 60px; */	
}

.spa--layout {
	display: flex;
	flex-direction: column;
	/* justify-content: space-between; */
	align-items: center;
}

Header {
	flex: 0 1 auto;

}

Footer {
	flex: 0 1 auto;
}

FirstPage {
	flex: 1 1 auto;
}

</style>
