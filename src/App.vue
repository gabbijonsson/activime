<template>
	<div id="app">
		<Header 
		@showHome="showHome($event)"
		@showsettings="showsettings($event)"/>
		<FirstPage @showBfSprint="showBeforeSprint($event)" v-if="showFirstPage"/>
		<BeforeSprint v-if="showBeforeSprint"/>
		<SettingsPage v-if="showSettings"/>
		<Footer/>
	</div>
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'
import FirstPage from './components/FirstPage'
import SettingsPage from './components/SettingsPage'
import BeforeSprint from './components/BeforeSprint'

export default {
	name: 'App',
	components: {
		Header,
		Footer,
		FirstPage,
		SettingsPage,
		BeforeSprint,
	},
	data: () => ({
		showSettings: false,
		showFirstPage: true,
		showBeforeSprint: false,
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
		},
		showBeforeSprint(event){
			console.log(event);
			this.showBeforeSprint = event;			
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
