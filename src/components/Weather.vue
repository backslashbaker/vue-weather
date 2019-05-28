<template>
    <div>
        <input type="text" placeholder="Enter City name" v-model="city">
        <button @click="getCurrentWeather()">Get current Weater</button>
        <div v-if="weatherDataReady" class="">
            <img :src="getImageUrl(weatherData.weather[0].icon)" />
            <p><strong>Description:</strong> {{weatherData.weather[0].description}}</p>
            <p><strong>Temperature:</strong> {{ kelvinToCelcius(weatherData.main.temp) }}°C</p>
            

        </div>
    </div>
</template>

<script>
import axios from 'axios'
const apikey = process.env.VUE_APP_API_KEY;
export default {
    name: "Weather",
    data() {
        return {
            city: null,
            weatherData: {

            },
            weatherDataReady: false,
           

        }
    },
    methods: {
        getCurrentWeather() {
            
            axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${apikey}`)
                .then((res) => {
                    this.weatherData = res.data;
                    this.weatherDataReady = true;

                    console.log(this.weatherData) 
                    })
                .catch((err) => console.log(err));
        },
         kelvinToCelcius(kelvin) {
            const kelvinDifference = 273.15
            const converted = kelvin - kelvinDifference;

            return Math.round(converted)
        },
        getImageUrl(icon){

        return `http://openweathermap.org/img/w/${icon}.png`

        },
    },
    mounted() {
        console.log(process.env);
    }

}
</script>

<style>

</style>
