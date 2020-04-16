<template>
  <div>
    <img :src='imgPath' />
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "WeatherInfo",
  data: () => ({
    imgPrefix: './images/icon--weather-',
    imgSuffix: ".svg",
    imgPath: "",
    location: 'Gothenburg',
	appKey: '9388362ecafd4f7bb4e210728200804&q=',
	baseURL: 'https://api.weatherapi.com/v1/current.json?key='
  }),
   created: function () {
    axios.get(this.baseURL + this.appKey + this.location)
    .then(response => response.data.current.condition.code)
    .then(weatherCode => { 
        let weather = this.getWeatherFromWeatherCode(weatherCode)
        this.imgPath = this.imgPrefix + weather + this.imgSuffix; 
        console.log(this.imgPath)
    });
   },
  methods: {
    getWeatherFromWeatherCode: function(weatherCode) {

      switch (weatherCode) {
        // Sunny
        case 1000: //Sunny skies/Clear skies
          return "sunny";
        // Sunny Clouds
        case 1003: //Partly cloudy skies
          return "sunnyclouds";
        // Clouds
        case 1006: //Cloudy skies
        case 1009: //Overcast skies
        case 1030: //Mist
        case 1135: //Fog
        case 1147: //Freezing fog
          return "clouds";
        // Showers
        case 1063: //Patchy rain possible
        case 1150: //Patchy light drizzle
        case 1153: //Light drizzle
        case 1072: //Patchy freezing drizzle possible
        case 1168: //Freezing drizzle
        case 1171: //Heavy freezing drizzle
        case 1180: //Patchy light rain
        case 1183: //Light rain
        case 1198: //Light freezing rain
        case 1240: //Light rain shower
        case 1186: //Moderate rain at times
        case 1189: //Moderate rain
        case 1201: //Moderate or heavy freezing rain
        case 1243: //Moderate or heavy rain shower
        case 1069: //Patchy sleet possible
        case 1204: //Light sleet
        case 1207: //Moderate or heavy sleet
        case 1249: //Light sleet showers
        case 1210: //Patchy light snow
        case 1213: //Light snow
        case 1255: //Light snow showers
        case 1066: //Patchy snow possible
        case 1216: //Patchy moderate snow
        case 1219: //Moderate snow
        case 1279: //Patchy light snow with thunder
          return "showers";
        // Storm
        case 1192: //Heavy rain at times
        case 1195: //Heavy rain
        case 1246: //Torrential rain shower
        case 1252: //Moderate or heavy sleet showers
        case 1258: //Moderate or heavy snow showers
        case 1114: //Blowing snow
        case 1222: //Patchy heavy snow
        case 1225: //Heavy snow
        case 1117: //Blizzard
        case 1237: //Ice pellets
        case 1261: //Light showers of ice pellets
        case 1264: //Moderate or heavy showers of ice pellets
        case 1273: //Patchy light rain with thunder
        case 1276: //Moderate or heavy rain with thunder
        case 1087: //Thundery outbreaks possible
        case 1282: //Moderate or heavy snow with thunder
          return "storm";
      }
    }
  }
};
</script>

<style scoped>
img {
    margin-top: 5em;
    height: 42px;
}
</style>