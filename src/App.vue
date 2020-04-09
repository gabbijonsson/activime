<template>
	<div id="app">
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
#app {
	font-family: Montserrat;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	/* text-align: center; */
	color: #2c3e50;
	/* margin-top: 60px; */	
}

</style>
