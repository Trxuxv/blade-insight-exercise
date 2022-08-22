<template>
  <div class="w-full h-screen bg-gradient-to-b from-gray-200 to-yellow-300">
    <Nav />
    <div class="w-full h-16 py-3 px-10">
      <form class="flex items-center w-3/6">
        <div class="select rounded-lg" tabindex="1">
          <input class="selectopt try-option rounded-lg" name="test" type="radio" id="opt1" checked>
          <label for="opt1" class="option bg-white">Oranges</label>
          <input class="selectopt try-option rounded-lg" name="test" type="radio" id="opt2">
          <label for="opt2" class="option bg-white">Apples</label>
          <input class="selectopt try-option rounded-lg" name="test" type="radio" id="opt3">
          <label for="opt3" class="option bg-white">Grapefruit</label>
          <input class="selectopt try-option rounded-lg" name="test" type="radio" id="opt4">
          <label for="opt4" class="option bg-white">Bananas</label>
          <input class="selectopt try-option rounded-lg" name="test" type="radio" id="opt5">
          <label for="opt5" class="option bg-white">Watermelon</label>
        </div>
        <label for="simple-search" class="sr-only">Search</label>
        <div class="relative w-full">
          <div class="flex absolute inset-y-0 left-0 items-center pl-3 pointer-events-none">
            <svg aria-hidden="true" class="w-5 h-5 text-gray-500 dark:text-gray-400" fill="currentColor"
              viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
              <path fill-rule="evenodd"
                d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                clip-rule="evenodd"></path>
            </svg>
          </div>
          <input type="text" id="simple-search"
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full pl-10 p-2.5  dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            placeholder="Search" required="">
        </div>
      </form>



    </div>
    <div class="grid grid-cols-5 h-5/6 overflow-y-scroll p-2 m-4 rounded-lg tab-countries">
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

.tab-countries {
  background-color: rgba(255, 255, 255, 0.823);
  height: 80%;
}

.select {
  display: flex;
  flex-direction: column;
  position: relative;
  width: 250px;
  height: 40px;
}

.option {
  padding: 0 30px 0 10px;
  min-height: 40px;
  display: flex;
  align-items: center;
  position: absolute;
  top: 0;
  width: 100%;
  pointer-events: none;
  order: 2;
  z-index: 1;
  transition: background .4s ease-in-out;
  box-sizing: border-box;
  overflow: hidden;
  white-space: nowrap;

}

.option:hover {
  background: #666;
}

.select:focus .option {
  position: relative;
  pointer-events: all;
}

.try-option {
  opacity: 0;
  position: absolute;
  left: -99999px;
}

.try-option:checked+label {
  order: 1;
  z-index: 2;
  background: #666;
  border-top: none;
  position: relative;
}

.try-option:checked+label:after {
  content: '';
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 5px solid white;
  position: absolute;
  right: 10px;
  top: calc(50% - 2.5px);
  pointer-events: none;
  z-index: 3;
}

.try-option:checked+label:before {
  position: absolute;
  right: 0;
  height: 40px;
  width: 40px;
  content: '';
  background: #666;
}
</style>
