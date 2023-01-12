<template>
  <div class="container">
    <h1>Weather App</h1>
    <search-input></search-input>
    <div class="">
      <img src="https://via.placeholder.com/400x300" class="time card-img-top" alt="" />
      <div class="icon bg-light mx-auto text-center">
        <!-- icon -->
        <img src="" alt="" />
      </div>
      <div class="details">
        <h5 class="">City name</h5>
        <div class="">Weather condition</div>
        <div class="">
          <span>temp</span>
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
