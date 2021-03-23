<template>
  <div class="five-container" :key="weather.visibility" v-for="weather in weatherFive">
      <div class="card" style="width: 18rem;">
  <div class="card-body">
    <h5 class="card-title">{{weather.dt_txt}}</h5>
    <h6 class="card-subtitle mb-2 text-muted">{{ Math.floor(weather.main.temp - 273.15)}}°C</h6>
    <p class="card-text">humidity: {{weather.main.humidity}}% </p>
    <p>wind-speed: {{weather.wind.speed}}mph</p>
    <p>pressure: {{weather.main.pressure}}mb</p>
  </div>
</div>
  </div>
</template>

<script>
export default {
  name: "FiveDay",
  props: {
    weatherFive: Object,
  },
};
</script>