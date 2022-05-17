<template>

    <main>
        MAIN

        <CardComp />
    </main>
  
</template>

<script>
import CardComp from './CardComp.vue';

export default {
    name: "MainComp",
    components: { CardComp }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars';

</style>