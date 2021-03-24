<template>
  <div class="weather">
    <img
      v-if="weather.weather[0].main === 'Clouds'"
      src="http://openweathermap.org/img/wn/03d.png"
      alt="clouds"
      class="icon"
    />
    <img
      v-if="weather.weather[0].main === 'Clear'"
      src="http://openweathermap.org/img/wn/01d.png"
      alt="clear"
      class="icon"
    />
    <img
      v-if="weather.weather[0].main === 'Drizzle'"
      src="http://openweathermap.org/img/wn/10d.png"
      alt="drizzle"
      class="icon"
    />
    <img
      v-if="weather.weather[0].main === 'Snow'"
      src="http://openweathermap.org/img/wn/13d.png"
      alt="snow"
      class="icon"
    />
    <img
      v-if="weather.weather[0].main === 'Rain'"
      src="http://openweathermap.org/img/wn/09d.png"
      alt="rain"
      class="icon"
    />
  </div>
</template>

<script>
export default {
  name: "Icons",
  props: {
    weather: Object,
  },
};
</script>

<style scoped>
.icon {
    height: 100px;
    width: 100px;
    position: relative;
    top: 18px;
}
</style>