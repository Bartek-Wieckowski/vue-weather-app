<template>
  <div class="container">
    <h1>Weather App</h1>
    <search-input @update:inputData="findLocationDetails($event)" @keypress="fetchWeather"></search-input>
    <div class="" v-if="!!details.main">
      <img :src="details.main.temp > 16 ? warmUrl : coldUrl" class="time card-img-top" alt="" />
      <div class="icon bg-light mx-auto text-center">
        <!-- icon -->
        <img src="" alt="" />
      </div>
      <div class="details">
        <h5 class="">{{ details.name }}, {{ details.sys.country }}</h5>
        <div class="">{{ details.weather[0].description }}</div>
        <div class="">
          <span>{{ Math.round(details.main.temp) }}</span>
          <span>&deg;C</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchInput from "./components/SearchInput.vue";

export default {
  name: "App",
  components: {
    SearchInput,
  },
  data() {
    return {
      locationSearched: "",
      details: {},
    };
  },
  computed: {
    warmUrl() {
      return require("./assets/warm-bg.jpg");
    },
    coldUrl() {
      return require("./assets/cold-bg.jpg");
    },
  },
  methods: {
    findLocationDetails(inputValue) {
      this.locationSearched = inputValue;
    },
    fetchWeather(e) {
      if (e.key === "Enter") {
        fetch(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.locationSearched}&units=metric&APPID=${process.env.VUE_APP_API_KEY}`
        )
          .then((res) => res.json())
          .then(this.showDetails);
      }
    },
    showDetails(results) {
      this.details = results;
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
.container {
  max-width: 400px;
  width: 100%;
  padding-right: 15px;
  padding-left: 15px;
  margin-right: auto;
  margin-left: auto;
  text-align: center;
}
h1 {
  color: #6c757d;
  margin: 25px auto;
}
.card-img-top {
  max-width: 100%;
}
.details {
  text-align: center;
  text-transform: uppercase;
  color: #6c757d;
}
</style>
