<template>
	<div></div>
</template>

<script>
import axios from 'axios'
export default {
	name: 'ApiHandler',
	mounted(){
		this.fetchWeather()
	},
	data: () => ({
		location: 'Gothenburg',
		appKey: '9388362ecafd4f7bb4e210728200804&q=',
		baseURL: 'https://api.weatherapi.com/v1/current.json?key=',
		weatherCode: Number,
		temp_C: Number,
	}),
	methods: {
		fetchWeather(){
			axios.get(this.baseURL + this.appKey + this.location)
			.then(Response => {
				console.log(Response);
				console.log(Response.data);
				this.weatherCode = Response.data.current.condition.code		//Lägger väderkoden i "weatherCode"
				this.temp_C = Response.data.current.temp_c			// Lägger temperaturen i "temp_C"
				console.log(this.weatherCode);
				console.log(this.temp_C);
				
				
			})
		},
	},
}
</script>

<style scoped>

</style>