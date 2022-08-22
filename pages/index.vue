<template>
  <div class="w-full h-screen">
    <Countries />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Countries from './countries/index.vue'

export default Vue.extend({
  name: 'IndexPage',
  components: {
    Countries
  }
})
</script>
