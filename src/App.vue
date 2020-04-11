<template>
	<div id="app">
		<Header 
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
#app {
	font-family: Montserrat;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	/* text-align: center; */
	color: #2c3e50;
	/* margin-top: 60px; */	
}
html{
		background-color: #bbdadf;
	}
</style>
