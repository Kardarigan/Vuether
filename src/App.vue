
<template>
  <main class="container h-screen p-5">
    <input type="text" class="field one-bg" placeholder="City...">
    <div class="text-center mt-12">
      <h2 class="title drop-shadow-xl">Toronto, Canada</h2>
      <h3 class="para">Tu, 17 September 2024</h3>
      <div class="one-bg p-12 my-5">
        <h1 class="title-lg drop-shadow-xl">3°<span class="italic">c</span></h1>
      </div>
      <h2 class="title">Foggy</h2>
    </div>
  </main>
</template>


<script>
  export default {
    name : "app",
    data () {
      return {
        api_key:"50e7bbbd70c0b2485807bafbe43dd6a4"
        url_base: "http://api.openweathermap.org/data/2.5/"
        query: "",
        weather: {}
    }
  }
</script>