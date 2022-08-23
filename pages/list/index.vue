<template>
  <div class="h-screen w-full bg-gradient-to-b from-gray-200 to-gray-600">
    <Nav />
    <div
      class="overflow-hidden h-5/6 shadow-md sm:rounded-lg w-4/6 text-center m-auto mt-10"
    >
      <div class="p-2 bg-gray-100 overflow-y-scroll tab pt-4">
        <thread class="w-full ">
          <tr class="w-full">
            <th>
              <select
                v-model="region"
                id="countries"
                class="bg-gray-50 text-left py-2.5 border pr-6 border-gray-300 text-gray-400 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full pl-10 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
              >
                <option selected=""><span> Choose a region </span></option>
                <option class="h-16 text-lg leading-8 text-white" value="africa">
                  Africa <span class="text-red-500"> a</span>
                </option>
                <option value="antarctic Ocean">Antarctic Ocean</option>
                <option value="antarctic">Antarctic</option>
                <option value="americas">America</option>
                <option value="asia">Asia</option>
                <option value="europe">Europe</option>
                <option value="oceania">Oceania</option>
              </select>
            </th>
            <th>
            <div class="w-10 h-full"></div>
            </th>
            <th>
              <form class="flex items-center">
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
                    v-model="search"
                    type="text"
                    id="simple-search"
                    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full pl-10 p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                    placeholder="Search"
                    required=""
                  />
                </div>
              </form>
            </th></tr
        ></thread>
        <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400 mt-6">
          <thead
            class="text-xs text-gray-700 uppercase bg-gray-100 dark:bg-gray-700 dark:text-gray-400 w-full"
          >
            <tr>
              <th scope="col" class="py-3 px-6 font-bold text-center">Flag</th>
              <th scope="col" class="py-3 px-6 font-bold text-center">Name</th>
              <th scope="col" class="py-3 px-6 font-bold text-center">Region</th>
              <th scope="col" class="py-3 px-6 font-bold text-center">Subregion</th>
              <th scope="col" class="py-3 px-6 font-bold text-center">Capital</th>
              <th scope="col" class="py-3 px-6 font-bold text-center">Population</th>
            </tr>
          </thead>
          <tbody v-for="item in filteredCountries">
            <tr
              v-show="!loading"
              class="bg-white border-b dark:bg-gray-900 dark:border-gray-700 text-center"
            >
              <th scope="row" class="py-4 px-4 bg-gray-50 text-center rounded-lg">
                <img :src="item.flag" class="w-12 mx-auto rounded-sm" alt="" />
              </th>
              <td class="py-4 px-6 text-center">
                {{ item.name }}
              </td>
              <td class="py-4 px-6">
                {{ item.region }}
              </td>
              <td class="py-4 px-6">
                {{ item.subregion }}
              </td>
              <td class="py-4 px-6">
                {{ item.capital }}
              </td>
              <td class="py-4 px-6">
                {{ item.population }}
              </td>
            </tr>
          </tbody>
        </table>
        <div class="w-full h-4/6 flex justify-center items-center" v-show="loading">
          <svg
            role="status"
            class="inline mr-2 w-12 h-12 text-gray-200 animate-spin dark:text-gray-600"
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
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import Vue from "vue";
import Nav from "~/components/Nav.vue";

export default Vue.extend({
  name: "List",
  data() {
    return {
      region: "Choose a region",
      loading: true,
      search: "",
      regions: [],
      countries: [],
    };
  },
  created() {
    fetch("https://restcountries.com/v2/all")
      .then((response) => response.json())
      .then((data) => {
        this.countries = data;
        this.loading = false;
      });
  },

  methods: {
    onChange(event) {
      alert(event.target.value);
    },
  },

  computed: {
    filteredCountries() {

      if (this.region === "Choose a region" && this.search != "") {
        return this.countries.filter((x: any) => {
          return x.name.toLowerCase().includes(this.search.toLowerCase());
        });
      }

      if (this.region != "Choose a region" || this.search != "") {
        return this.countries.filter((x: any) => {
          return (
            x.region.toLowerCase().includes(this.region.toLowerCase()) &&
            x.name.toLowerCase().includes(this.search.toLowerCase())
          );
        });
      }

      if (this.region === "Choose a region" && this.search === "") {
        return this.countries.filter((x: any) => {
          return (
            x.region.toLowerCase().includes("") ||
            x.name.toLowerCase().includes(this.search.toLowerCase())
          );
        });
      }

    },
  },
  components: { Nav },
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
  background: red;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb:hover {
  background: red;
}

.tab {
  height: 100%;
}
</style>
