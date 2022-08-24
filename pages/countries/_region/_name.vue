<template>
  <div class="w-full h-screen bg-gradient-to-b from-gray-200 to-gray-600">
    <Nav />
    <div v-show="!loading" class="w-5/6 bg-white h-4/6 mx-auto rounded-lg mt-8 overflow-hidden">
      <div class="w-4/6 float-left h-full vector" :style="{
        'background-image': `url(${country?.flag})`,
      }">
        <img class="w-full bottom-0 rounded-lg" src="./../../../static/vector-2.png" />
      </div>
      <div class="w-2/6 float-right h-full bg-gray-600 rounded-r-lg px-8">
        <h3 class="text-2xl text-center font-semibold mt-4 mb-2">{{ country?.name }}</h3>
        <h4 class="text-right text-sm">
          Original name: <b>{{ country?.nativeName }}</b>
        </h4>
        <div class="w-full h-16 mt-6 grid grid-cols-4 rounded-lg">
          <div class="text-center h-4/5 bg-gray-300 my-1 py-4 text-sm rounded-l-lg">
            Capital:
          </div>
          <div class="text-center h-4/5 bg-gray-200 py-4 text-sm font-semibold">
            {{ country?.capital }}
          </div>
          <div class="text-center h-4/5 bg-gray-300 my-1 py-4 text-sm">Flag:</div>
          <div class="text-center h-4/5 bg-gray-200 px-7 py-1.5 text-sm font-semibold rounded-r-lg">
            <img class="w-16" :src="country?.flag" />
          </div>
        </div>

        <div class="w-full bg-gray-400 h-28 mt-10 rounded-lg grid grid-cols-4">
          <div class="text-sm text-center flex justify-center font-semibold items-center">
            Region:
          </div>
          <div class="text-sm text-center flex justify-center items-center">
            {{ country?.region }}
          </div>
          <div class="text-sm text-center flex justify-center font-semibold items-center">
            Subregion:
          </div>
          <div class="text-sm text-center flex justify-center items-center">
            {{ country?.subregion }}
          </div>
          <div class="text-sm text-center flex justify-center font-semibold items-center">
            Population:
          </div>
          <div class="text-sm text-center flex justify-center items-center">
            {{ country?.population }}
          </div>
          <div class="text-sm text-center flex justify-center font-semibold items-center">
            Area:
          </div>
          <div class="text-sm text-center flex justify-center items-center">
            {{ country?.area }}
          </div>
          <div class="text-sm text-center flex justify-center font-semibold items-center">
            Demonym:
          </div>
          <div class="text-sm text-center flex justify-center items-center">
            {{ country?.demonym }}
          </div>
          <div class="text-sm text-center flex justify-center font-semibold items-center">
            Independent:
          </div>
          <div class="text-sm text-center flex justify-center items-center">
            {{ country?.independent ? "Yes" : "No" }}
          </div>
        </div>

        <div v-show="!country?.borders"
          class="mt-14 rounded-lg w-full text-center h-1/5 bg-white flex items-center justify-center">
          <b class="text-base">This country does not have borders :'0 </b>
        </div>
        <div v-show="country?.borders"
          class="mt-14 rounded-lg w-full text-center h-1/5 bg-white grid grid-cols-5 gap-2 p-3">
          <b class="text-base">Borders: </b>
          <div
            class="h-8 flex items-center cursor-pointer text-gray-100 font-bold justify-center text-sm rounded-full text-center bg-yellow-600"
            v-for="item in country?.borders" :key="item">
            {{ item }}
          </div>
        </div>
      </div>
    </div>
    <div v-show="loading" class="w-5/6 bg-white h-4/6 rounded-lg flex items-center justify-center mx-auto mt-10">
      <svg role="status" class="inline mr-2 w-12 h-12 text-gray-200 animate-spin dark:text-gray-600"
        viewBox="0 0 100 101" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path
          d="M100 50.5908C100 78.2051 77.6142 100.591 50 100.591C22.3858 100.591 0 78.2051 0 50.5908C0 22.9766 22.3858 0.59082 50 0.59082C77.6142 0.59082 100 22.9766 100 50.5908ZM9.08144 50.5908C9.08144 73.1895 27.4013 91.5094 50 91.5094C72.5987 91.5094 90.9186 73.1895 90.9186 50.5908C90.9186 27.9921 72.5987 9.67226 50 9.67226C27.4013 9.67226 9.08144 27.9921 9.08144 50.5908Z"
          fill="currentColor"></path>
        <path class="text-5xl"
          d="M93.9676 39.0409C96.393 38.4038 97.8624 35.9116 97.0079 33.5539C95.2932 28.8227 92.871 24.3692 89.8167 20.348C85.8452 15.1192 80.8826 10.7238 75.2124 7.41289C69.5422 4.10194 63.2754 1.94025 56.7698 1.05124C51.7666 0.367541 46.6976 0.446843 41.7345 1.27873C39.2613 1.69328 37.813 4.19778 38.4501 6.62326C39.0873 9.04874 41.5694 10.4717 44.0505 10.1071C47.8511 9.54855 51.7191 9.52689 55.5402 10.0491C60.8642 10.7766 65.9928 12.5457 70.6331 15.2552C75.2735 17.9648 79.3347 21.5619 82.5849 25.841C84.9175 28.9121 86.7997 32.2913 88.1811 35.8758C89.083 38.2158 91.5421 39.6781 93.9676 39.0409Z"
          fill="red"></path>
      </svg>
      <span class="text-base mt-2 font-bold text-gray-500 cursor-pointer">
        Loading...
      </span>
    </div>
  </div>
</template>
<script lang="ts">
import { CountryModel } from "../model/country.model";
import Nav from "./../../../components/Nav.vue";
import useRoute from "vue-router";
import Vue from "vue";

export default Vue.extend({
  name: "Country",
  data() {
    return {
      param: this.$route.params,
      region: "Choose a region",
      loading: true,
      search: "",
      countries: [] as CountryModel[],
    };
  },

  created() {
    fetch("https://restcountries.com/v2/all")
      .then((response) => response.json())
      .then((data) => {
        if (typeof window !== 'undefined') {
          localStorage.setItem("countries", JSON.stringify(data))
        }
        (this.countries = data), (this.loading = false);
      });
  },

  computed: {
    country() {
      if (typeof window !== 'undefined') {
        let countries = JSON.parse(localStorage.getItem('countries')!);

        return countries.find((x: CountryModel) =>
          x.name.toLowerCase() == this.param.name &&
          x.region.toLowerCase() == this.param.region
        );
      }
    },
  },
  components: { Nav },
});
</script>

<style>
.vector {
  background-size: cover;
  background-repeat: no-repeat;
}
</style>
