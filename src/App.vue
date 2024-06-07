<template>
  <div id="body" :class="typeof weather.main != 'undefined' ? weather.weather[0].main : 'Clear'">
    <main class="bg-slate-900 bg-opacity-50">
      <section class="container h-screen p-5">
        <input type="text" class="field one-bg" placeholder="City..." v-model="query" @keypress="fetchWeather">
        <div class="text-center mt-12" v-if="typeof weather.main != 'undefined'">
          <h2 class="title drop-shadow-xl">{{ weather.name + " , " + weather.sys.country }}</h2>
          <h3 class="para">{{ dateBuilder() }}</h3>
          <div class="one-bg p-12 my-5 flex justify-center">
            <h1 class="title-lg drop-shadow-xl ms-2">{{ Math.round(weather.main.temp) }}</h1>
            <span class="italic font-thin opacity-70 text-xl">°c</span>
          </div>
          <h2 class="title">{{ weather.weather[0].main }}</h2>
        </div>
      </section>
    </main>
  </div>
</template>


<script>
export default {
  name: "app",
  data() {
    return {
      api_key: "50e7bbbd70c0b2485807bafbe43dd6a4",
      url_base: "http://api.openweathermap.org/data/2.5/",
      query: "calgary",
      weather: {}
    }
  },
  mounted() {
    fetch(`${this.url_base}weather?q=${this.query}&units=metric&appid=${this.api_key} `)
      .then(res => {
        return res.json();
      }).then(this.setResults);
  },
  methods: {
    fetchWeather(e) {
      if (e.key == "Enter") {
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&appid=${this.api_key} `)
          .then(res => {
            return res.json();
          }).then(this.setResults);
      }
    },
    setResults(results) {
      this.weather = results;
    },
    dateBuilder() {
      let d = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      let days = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();

      return `${date} ${day} ${month} ${year}`;
    }
  }
}
</script>