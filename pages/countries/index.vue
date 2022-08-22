<template>
  <div class="w-full h-screen bg-gradient-to-b from-gray-200 to-yellow-300">
    <Nav />
    <div class="grid grid-cols-5 h-5/6 overflow-y-scroll p-2 m-4 rounded-lg tab">
      <div class="max-w-sm rounded shadow-lg m-5" v-for="item in countries">
        <img class="w-full h-2/5" :src="item.flag" alt="Sunset in the mountains">
        <div class="px-6 py-4">
          <div class="font-bold text-xl mb-2">{{ item.name }}</div>
          <p class="text-gray-700 text-base">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptatibus quia, nulla! Maiores et perferendis
            eaque, exercitationem praesentium nihil.
          </p>
        </div>
        <div class="px-6 pt-4 pb-2">
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#{{
                item.region
            }}</span>
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#{{
                item.capital
            }}</span>
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#winter</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'Countries',
  data() {
    return {
      countries: []
    }
  },

  created() {
    fetch("https://restcountries.com/v2/all")
      .then(response => response.json())
      .then(data => { localStorage.setItem("countries", data), console.log(data), (this.countries = data) });
  }
})
</script>
<style>
::-webkit-scrollbar {
  width: 10px;
}

::-webkit-scrollbar-track {
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  background: #f88c56;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb:hover {
  background: #f88c56;
}

.tab{
  background-color: rgba(255, 255, 255, 0.823);
  height: 90%;
}
</style>
