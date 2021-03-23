<template>
  <div id="app">
    <main>
      <div class="bar">
        <input
          type="text"
          class="search-bar"
          placeholder="Search a city..."
          v-model="query"
          @keypress="fetchWeather"
        />
      </div>
      <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
        <div class="location-box">
          <div class="location">
            <div class="weather">{{ weather.weather[0].main }}</div>
            {{ weather.name }}, {{ weather.sys.country }}
          </div>
          <div class="date">{{ dateBuilder() }}</div>
        </div>
      </div>
      <div class="weather-box" v-if="typeof weather.main != 'undefined'">
        <div class="temp">{{ Math.round(weather.main.temp) }}°C</div>
      </div>
      <FiveDay :weatherFive="weatherFive" />
    </main>
  </div>
</template>

<script>
import axios from "axios";
import FiveDay from "./components/FiveDay.vue";
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  name: "App",
  components: {
    FiveDay,
  },
  data() {
    return {
      api_key: "2bbd84d695f75e90260a321f5b80b8b5",
      url_base: "https://api.openweathermap.org/data/2.5/",
      url_five: "https://api.openweathermap.org/data/2.5/forecast?q=",
      query: "london",
      weather: {},
      weatherFive: {},
    };
  },
  methods: {
    async fetchWeather(e) {
      if (e.key == "Enter") {
        try {
          const response1 = await axios.get(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`);
          this.weather = response1.data;
          const response2 = await axios.get(
            `${this.url_five}${this.query}&appid=${this.api_key}`
          );
          console.log(response2.data)
          this.weatherFive = response2.data.list;
        } catch (e) {
          console.log(e);
        }
      }
    },
    dateBuilder() {
      let d = new Date();
      let months = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];
      let days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ];
      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();
      return `${day} ${date} ${month} ${year}`;
    },
  },
};
</script>

<style>
.bar {
  text-align: center;
  margin-top: 8%;
}

input {
  height: 33px;
  width: 20%;
  border-radius: 12px;
  border: none;
  padding-left: 8px;
  box-shadow: 0 0 4pt 2pt #d3d3d3;
}

.location-box,
.weather-box {
  text-align: center;
}
.temp {
  font-weight: bold;
  font-size: 80px;
}
</style>