<template>
	<div id="app">
		<Header class="spa--layout"
		@showHome="showHome($event)"
		@showsettings="showsettings($event)"/>
		<FirstPage v-if="showFirstPage"/>
		<SettingsPage v-if="showSettings"/>
		<Footer/>
	</div>
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'
import FirstPage from './components/FirstPage'
import SettingsPage from './components/SettingsPage'

export default {
	name: 'App',
	components: {
		Header,
		Footer,
		FirstPage,
		SettingsPage,
	},
	data: () => ({
		showSettings: false,
		showFirstPage: true,
	}),
	methods: {
		showHome(event){
			console.log(event);
			this.showSettings = event.settings;
			this.showFirstPage = event.firstpage;
		},
		showsettings(event){
			console.log(event);
			this.showSettings = event.settings;
			this.showFirstPage = event.firstpage;
		}
	},
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat&display=swap');

* {
	box-sizing: border-box;
}

body, html {
	margin: 0;
	padding: 0;
}

#app {
	font-family: 'Montserrat', sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: #2c3e50;
	width: 100vw;
	height: 100vh;
}

.spa--layout {
	display: flex;
	flex-direction: column;
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
