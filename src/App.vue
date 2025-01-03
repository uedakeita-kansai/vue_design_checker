<template>
  <v-app>
    <v-main>
      <test-component/>
    </v-main>
  </v-app>
</template>

<script>
import TestComponent from './components/TestComponent.vue'

export default {
  name: 'App',

  components: {
    TestComponent,
  },

  data: () => ({
    //
  }),
}
</script>

<style>
  #appvueid{
    color: rgb(255, 247, 0);
  }
  .appvueclass{
    color: rgb(0, 255, 0);
  }
  #appvueidimportant{
    color: rgb(165, 160, 0) !important;
  }
  .appvueclassimportant{
    color: rgb(0, 128, 0)  !important;
  }
</style>