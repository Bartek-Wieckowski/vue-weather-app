<template>
  <div class="change-location">
    <label for="city">Enter a location for weather information</label>
    <input
      type="text"
      name="city"
      id="city"
      class="input-search"
      :value="inputData"
      @input="$emit('update:inputData', $event.target.value)"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputData: "",
    };
  },
  emits: ["update:inputData"],
};
</script>

<style scoped>
.change-location {
  margin: 25px auto;
}
label {
  display: inline-block;
  margin-bottom: 0.5rem;
}
.input-search {
  display: block;
  width: 100%;
  height: calc(1.5em + 0.75rem + 2px);
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #495057;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}
</style>
