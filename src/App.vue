<template>

	<div id="app" class="spa--layout">
		<Header 
		@showHome="showHome($event)"
		@showsettings="showsettings($event)"/>
		<WeatherInfo v-if="weatherIconEnabled" />
		<FirstPage @showBfSprint="showBfSprint($event)" v-if="showFirstPage"/>
		<div v-if="showBeforeSprint">
			<h2>Vilken uppgift vill du jobba med idag?</h2>
			<BeforeSprint @showDuring="showthisDuring($event)"/>
		</div>
		<div v-if="showFinishedTasks">
			<h1>JIPPI!</h1>
			<H3>Du har hunnit med en hel del idag!</H3>
			<FinishedTasks/>
		</div>

		
		<DuringSprint v-if="showDuringSprint"/>
		<WorkListDisplay v-show="!hidden"/>

		<SettingsPage @checkboxOnOff="toggleWeather($event)" v-if="showSettings"/>


		<Footer/>
	</div>
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'
import FirstPage from './components/FirstPage'
import SettingsPage from './components/SettingsPage'
import BeforeSprint from './components/BeforeSprint'
import FinishedTasks from './components/FinishedTasks'
import WorkListDisplay from './components/WorkListDisplay'
import DuringSprint from './components/DuringSprint'
import WeatherInfo from './components/WeatherInfo'


export default {
	name: 'App',
	components: {
		Header,
		Footer,
		FirstPage,
		SettingsPage,
		BeforeSprint,
		DuringSprint,
		FinishedTasks,

		WorkListDisplay,

		WeatherInfo


	},
	data: () => ({
		hidden: true,
		showDuringSprint: false,
		showSettings: false,
		showFirstPage: true,
		showBeforeSprint: false,
		showFinishedTasks: false,
		showThisDuring: false,
		weatherIconEnabled: true,
		
	}),
	methods: {
		showHome(event){
			console.log(event);
			this.showSettings = event.settings;
			this.showFirstPage = event.firstpage;
			this.showBeforeSprint = false
			this.showFinishedTasks = false
			this.showDuringSprint = false
		},
		showsettings(event){
			console.log(event);
			this.showSettings = event.settings;
			this.showFirstPage = event.firstpage;
			this.showBeforeSprint = false
			this.showFinishedTasks = false
			this.showDuringSprint = false
		},
		showBfSprint(event){
			console.log(event);
			this.showBeforeSprint = event;
			this.showSettings = false;
			this.showFirstPage = false;

			this.showDuringSprint = false
		},
		showthisDuring(event){
			console.log('Inside the cursed app.vue', event);
			this.showDuringSprint = event;
			this.showBeforeSprint = false

		},
		toggleWeather(event){
			this.weatherIconEnabled = event;

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
	z-index: 2;
	position: relative;

}

Footer {
	flex: 0 1 auto;
	z-index: 2;
	position: relative;
}

FirstPage {
	flex: 1 1 auto;
}


html{
		background-color: #bbdadf;
	}
h2{
	margin-top: 5em;
	margin-bottom: 4em;
	text-decoration: underline;
	text-align: center;
}
h1, h3{
	text-align: center;
}

</style>
