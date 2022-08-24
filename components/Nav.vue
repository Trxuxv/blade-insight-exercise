<template>
  <div class="w-full flex items-center justify-center text-center text-sm h-16">
    <div class="w-4/5 h-full flex justify-center items-center">
      <div class="w-1/6 h-full flex justify-center items-center">
        <img class="w-10" src="http://cdn.onlinewebfonts.com/svg/img_260445.png" alt="">
      </div>
    </div>
    <div class="w-3/6 h-full flex justify-center items-center">
      <nuxt-link class="w-1/6 cursor-pointer" to="/">Home</nuxt-link>
      <nuxt-link class="w-1/6 cursor-pointer" to="/list">List</nuxt-link>
           <nuxt-link class="w-1/6 cursor-pointer" to="/map">Map</nuxt-link>
      <nuxt-link class="w-1/6 cursor-pointer" to="/about">About</nuxt-link>
      <a href="https://debora.netlify.app/" class="w-1/6 cursor-pointer" target="_blank">Débora L. F. Maciel</a>
      <!-- <nuxt-link class="w-1/6 cursor-pointer" to="/dev">
        Débora L. F. Maciel
      </nuxt-link> -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'Nav'
}
</script>
