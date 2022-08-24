<template>
    <div class="w-full h-screen bg-gradient-to-b from-gray-200 to-gray-600">
        <div class="w-full h-full mx-auto map">
            <div class="w-full pt-3 pl-2">
                <button type="button" href="/" @click="goHome"
                    class="text-white flex justify-center items-center bg-red-400 hover:bg-red-500 focus:outline-none font-medium rounded-full text-sm px-5 py-2.5 text-center mr-2 mb-2">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                        stroke="currentColor" class="w-6 h-6 mr-2">
                        <path stroke-linecap="round" stroke-linejoin="round"
                            d="M11.25 9l-3 3m0 0l3 3m-3-3h7.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                    </svg>
                    Back to home...</button>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
    name: "Map",
    methods: {
        goHome() {
            this.$router.push('/');
        }
    }
});
</script>
<style lang="css" scoped>
.map {
    background-image: url('./../../static/vector-3.jpg');
    background-size: contain;
}
</style>