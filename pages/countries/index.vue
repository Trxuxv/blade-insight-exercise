<template>
  <div class="w-full h-screen bg-gradient-to-b from-gray-200 to-yellow-300">
    <Nav />
    <div class="w-full h-16 py-3 px-10">
      <form class="flex items-center w-3/6">
        <div class="select rounded-lg" tabindex="1">
          <input
            class="selectopt try-option rounded-lg"
            name="test"
            type="radio"
            id="opt1"
            checked
          />
          <label for="opt1" class="option bg-white">Oranges</label>
          <input
            class="selectopt try-option rounded-lg"
            name="test"
            type="radio"
            id="opt2"
          />
          <label for="opt2" class="option bg-white">Apples</label>
          <input
            class="selectopt try-option rounded-lg"
            name="test"
            type="radio"
            id="opt3"
          />
          <label for="opt3" class="option bg-white">Grapefruit</label>
          <input
            class="selectopt try-option rounded-lg"
            name="test"
            type="radio"
            id="opt4"
          />
          <label for="opt4" class="option bg-white">Bananas</label>
          <input
            class="selectopt try-option rounded-lg"
            name="test"
            type="radio"
            id="opt5"
          />
          <label for="opt5" class="option bg-white">Watermelon</label>
        </div>
        <label for="simple-search" class="sr-only">Search</label>
        <div class="relative w-full">
          <div
            class="flex absolute inset-y-0 left-0 items-center pl-3 pointer-events-none"
          >
            <svg
              aria-hidden="true"
              class="w-5 h-5 text-gray-500 dark:text-gray-400"
              fill="currentColor"
              viewBox="0 0 20 20"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                clip-rule="evenodd"
              ></path>
            </svg>
          </div>
          <input
            type="text"
            id="simple-search"
            v-model="search"
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full pl-10 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            placeholder="Search"
            required=""
          />
        </div>
      </form>
    </div>
    <div
      v-if="loading"
      class="h-5/6 overflow-y-scroll p-2 m-4 rounded-lg tab-countries flex flex-col justify-center items-center"
    >
      <svg
        role="status"
        class="inline mr-2 w-16 h-16 text-gray-200 animate-spin dark:text-gray-600"
        viewBox="0 0 100 101"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M100 50.5908C100 78.2051 77.6142 100.591 50 100.591C22.3858 100.591 0 78.2051 0 50.5908C0 22.9766 22.3858 0.59082 50 0.59082C77.6142 0.59082 100 22.9766 100 50.5908ZM9.08144 50.5908C9.08144 73.1895 27.4013 91.5094 50 91.5094C72.5987 91.5094 90.9186 73.1895 90.9186 50.5908C90.9186 27.9921 72.5987 9.67226 50 9.67226C27.4013 9.67226 9.08144 27.9921 9.08144 50.5908Z"
          fill="currentColor"
        ></path>
        <path
          class="text-5xl"
          d="M93.9676 39.0409C96.393 38.4038 97.8624 35.9116 97.0079 33.5539C95.2932 28.8227 92.871 24.3692 89.8167 20.348C85.8452 15.1192 80.8826 10.7238 75.2124 7.41289C69.5422 4.10194 63.2754 1.94025 56.7698 1.05124C51.7666 0.367541 46.6976 0.446843 41.7345 1.27873C39.2613 1.69328 37.813 4.19778 38.4501 6.62326C39.0873 9.04874 41.5694 10.4717 44.0505 10.1071C47.8511 9.54855 51.7191 9.52689 55.5402 10.0491C60.8642 10.7766 65.9928 12.5457 70.6331 15.2552C75.2735 17.9648 79.3347 21.5619 82.5849 25.841C84.9175 28.9121 86.7997 32.2913 88.1811 35.8758C89.083 38.2158 91.5421 39.6781 93.9676 39.0409Z"
          fill="red"
        ></path>
      </svg>
      <span class="text-base mt-2 font-bold text-gray-500 cursor-pointer">
        Loading...
      </span>
    </div>
    <div
      v-if="!loading"
      class="grid grid-cols-5 h-5/6 overflow-y-scroll p-2 m-4 rounded-lg tab-countries"
    >
      <div class="max-w-sm rounded shadow-lg m-5" v-for="item in filteredItems">
        <img class="w-full h-2/5" :src="item.flag" alt="Sunset in the mountains" />
        <div class="px-6 py-4">
          <div class="font-bold text-xl mb-2">{{ item.name }}</div>
          <p class="text-gray-700 text-base">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptatibus quia,
            nulla! Maiores et perferendis eaque, exercitationem praesentium nihil.
          </p>
        </div>
        <div class="px-6 pt-4 pb-2">
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
            >#{{ item.region }}</span
          >
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
            >#{{ item.capital }}</span
          >
          <span
            class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
            >#winter</span
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "Countries",
  data() {
    return {
      loading: true,
      search: "",
      countries: [],
    };
  },

  created() {
    fetch("https://restcountries.com/v2/all")
      .then((response) => response.json())
      .then((data) => {
        console.log(data), (this.countries = data), (this.loading = false);
      });
  },
  computed: {
    filteredItems() {
      return this.countries.filter((x: any) => {
        return x.name.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },
});
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
  transition: background 0.4s ease-in-out;
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

.try-option:checked + label {
  order: 1;
  z-index: 2;
  background: #666;
  border-top: none;
  position: relative;
}

.try-option:checked + label:after {
  content: "";
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

.try-option:checked + label:before {
  position: absolute;
  right: 0;
  height: 40px;
  width: 40px;
  content: "";
  background: #666;
}
</style>
