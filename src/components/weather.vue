<template>
  <div class="search">
    <input
      type="text"
      class="search-bar"
      placeholder="Search me.."
      v-model="loc"
      v-on:keypress="getcity"
    />
  </div>

  <div class="weather" v-if="typeof cond.main != 'undefined'">
    <div class="country">
      <div class="location">{{ cond.name }},{{ cond.sys.country }}</div>
      <div class="date">16th August 2021,Thurday</div>
    </div>

    <div class="conditions">
      <div class="temp">{{ cond.main.temp }}°C</div>
      <div class="rain">{{ cond.weather[0].main }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "weather",
  created() {
    navigator.geolocation.getCurrentPosition((success) => {
      this.cord.lat = success.coords.latitude;
      this.cord.long = success.coords.longitude;
      this.getcitybylocation();
    });
  },

  data() {
    return {
      loc: "",
      api_key: "3d9e1f2897d0c3617f1fb6c17b4d51bf",
      url_base: "https://api.openweathermap.org/data/2.5/",
      cond: {},
      cord: {
        lat: "",
        long: "",
      },
    };
  },

  methods: {
    getcity(e) {
      if (e.key == "Enter") {
        fetch(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.loc}&units=metric&appid=${this.api_key}`
        )
          .then((res) => {
            return res.json();
          })
          .then(this.setResults);
      }
    },

    getcitybylocation() {
      fetch(
        `https://api.openweathermap.org/data/2.5/weather?lat=${this.cord.lat}&lon=${this.cord.long}&units=metric&appid=${this.api_key}`
      )
        .then((res) => {
          return res.json();
        })
        .then(this.setResults);
    },

    setResults(results) {
      this.cond = results;
    },
  },
};
</script>

<style scoped>
.search {
  width: 100%;
  margin-top: 50px;
  padding: 0 25%;
}

.search-bar {
  display: block;
  width: 100%;
  padding: 15px;

  background: none;
  border: none;
  appearance: none;
  outline: none;
  border-radius: 0px 16px 0px 16px;
  background-color: rgb(140 140 140 / 21%);
  box-shadow: 3px 7px 7px -1px rgb(101 38 101 / 50%);

  color: rgb(130 22 84);
  font-size: 18px;
}

.search-bar:focus {
  background-color: rgb(140 140 140 / 40%);
}

.weather {
  text-align: center;
  padding-top: 20px;
}
.location {
  font-size: 30px;
  font-weight: bolder;
  color: black;
}
.date {
  font-size: 14px;
  font-weight: 800;
  color: black;
}
.temp {
  display: inline-block;
  font-size: 50px;
  font-weight: 900;
  color: black;
  text-shadow: 3px 5px rgba(0, 0, 0, 0.25);
}
.rain {
  font-size: 30px;
  font-weight: 800;
  color: black;
}
</style>>


