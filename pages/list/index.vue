<template>
  <div class="h-full w-full bg-gradient-to-b from-purple-200 to-pink-00">
    <Nav />
    <div class="overflow-x-auto relative shadow-md sm:rounded-lg w-4/6 text-center m-auto mt-10">
      <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
        <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400 ">
          <tr>
            <th scope="col" class="py-3 px-6 font-bold">
              Name
            </th>
            <th scope="col" class="py-3 px-6 font-bold">
              Region
            </th>
            <th scope="col" class="py-3 px-6 font-bold">
              Capital
            </th>
            <th scope="col" class="py-3 px-6 font-bold">
              Flag
            </th>
            <th scope="col" class="py-3 px-6 font-bold">
              Population
            </th>
          </tr>
        </thead>
        <tbody v-for="item in countries">
          <tr class="bg-white border-b dark:bg-gray-900 dark:border-gray-700">
            <th scope="row" class="py-4 px-6 font-medium text-gray-900 whitespace-nowrap dark:text-white">
              {{ item.name }}
            </th>
            <td class="py-4 px-6">
              {{ item.region }}
            </td>
            <td class="py-4 px-6">
              {{ item.capital }}
            </td>
            <td class="py-2 px-6">
              <img :src="item.flag" class="w-12 " alt="">
            </td>
            <td class="py-4 px-6">
              {{ item.population }}
            </td>
          </tr>
        </tbody>
      </table>
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
