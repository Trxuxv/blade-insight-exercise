<template>
  <div class="h-screen w-full bg-gradient-to-b from-gray-200 to-yellow-300">
    <Nav />
    <div class="overflow-hidden h-5/6 shadow-md sm:rounded-lg w-4/6 text-center m-auto mt-10">
      <div class="p-2 bg-gray-100 overflow-y-scroll tab">
        <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
          <thead class="text-xs text-gray-700 uppercase bg-gray-100 dark:bg-gray-700 dark:text-gray-400 w-full">
            <tr>
              <th scope="col" class="py-3 px-6 font-bold">
                Flag
              </th>
              <th scope="col" class="py-3 px-6 font-bold">
                Name
              </th>
              <th scope="col" class="py-3 px-6 font-bold">
                Capital
              </th>
              <th scope="col" class="py-3 px-6 font-bold">
                Region
              </th>
              <th scope="col" class="py-3 px-6 font-bold">
                Population
              </th>
            </tr>
          </thead>
          <tbody v-for="item in countries">
            <tr class="bg-white border-b dark:bg-gray-900 dark:border-gray-700">
              <th scope="row" class="py-4 px-4 bg-gray-50 text-center rounded-lg">
                <img :src="item.flag" class="w-12 mx-auto rounded-sm" alt="">
              </th>
              <td class="py-4 px-6">
                {{ item.name }}
              </td>
              <td class="py-4 px-6">
                {{ item.region }}
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
      </div>

    </div>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
import Nav from '~/components/Nav.vue';

export default Vue.extend({
  name: "List",
  data() {
    return {
      countries: []
    };
  },
  created() {
    fetch("https://restcountries.com/v2/all")
      .then(response => response.json())
      .then(data => { localStorage.setItem("countries", data), (this.countries = data); });
  },
  components: { Nav }
})
</script>


<style>
::-webkit-scrollbar {
  width: 17px;
}

::-webkit-scrollbar-track {
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  background: #c68f06;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb:hover {
  background: #f88c56;
}

.tab {
  height: 100%;
}
</style>
