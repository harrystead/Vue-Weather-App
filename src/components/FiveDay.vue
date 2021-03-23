<template>
  <div className="card-group">
    <div
      class="five-container"
      :key="weather.visibility"
      v-for="weather in weatherFive"
    >
      <div class="card" style="width: 12rem">
        <div class="card-body">
          <h5 class="card-title">{{ weather.dt_txt.slice(0, 10) }}</h5>
          <h6 class="card-subtitle mb-2">
            {{ Math.floor(weather.main.temp - 273.15) }}°C
          </h6>
          <small class="text-muted"
            >humidity: {{ weather.main.humidity }}%</small
          >
          <hr />
          <small class="text-muted"
            >wind-speed: {{ weather.wind.speed }}mph</small
          >
          <hr />
          <small class="text-muted"
            >pressure: {{ weather.main.pressure }}mb</small
          >
        </div>
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

<style scoped>
.card-group {
  text-align: center;
  margin: auto;
  position: absolute;
  left: 18%;
}

.five-container {
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
}
.card {
  border-radius: 15px;
  margin-right: 10px;
  display: inline-block;
  box-shadow: 0 0 2pt 0.2pt #d3d3d3;
}
hr {
  margin: 0px;
  margin-top: 5px;
}
.card-title {
  font-size: 14px;
}
.card-subtitle {
  font-size: 22px;
  font-weight: bold;
}
</style>