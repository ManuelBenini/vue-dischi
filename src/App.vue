<template>

  <div>
    <MainComp />
  </div>

</template>

<script>
import MainComp from './components/MainComp.vue';


export default {
  name: 'App',
  components: {
    MainComp
  }
}
</script>

<style lang="scss">
@import './assets/style/vars';
@import './assets/style/global';

</style>
