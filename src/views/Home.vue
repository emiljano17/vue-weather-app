<template>
  <div class="home">
    <form class="form-inline my-2 my-lg-0 d-flex">
      <input
        class="form-control mr-sm-2"
        type="search"
        placeholder="Country"
        aria-label="Search"
        @keyup.enter="search"
      />
      <button class="btn btn-outline-success my-2 my-sm-0" type="submit">
        Search
      </button>
    </form>
    <Weather :w="data" v-if="data != null" />
    <p>Search for a country to get weather information.</p>
    <p>API Docs: <a href="https://www.weatherapi.com/docs/">API WEATHER</a></p>
  </div>
</template>

<script>
// @ is an alias to /src
import Weather from "../components/Weather.vue";

export default {
  name: "Home",
  components: {
    Weather,
  },

  data() {
    return {
      query: "",
      data: null,
    };
  },

  methods: {
    search(e) {
      this.query = e.target.value;
      const result = {};

      fetch(
        "http://api.weatherapi.com/v1/current.json?key=2dce8c59b1994fe9b59153202201910&q=" +
          this.query
      )
        .then((response) => response.json())
        .then((data) => {
          result.country = data.location.country;
          result.region = data.location.region;
          result.tempc = data.current.temp_c;
          result.tempf = data.current.temp_f;
          result.lastupdated = data.current.last_updated;
          result.status = data.current.condition.text;
          result.icon = data.current.condition.icon;
          result.wind = data.current.wind_mph;
          result.humidity = data.current.humidity;

          this.data = result;
        })
        .catch((e) => console.log(e));
    },
  },
};
</script>
