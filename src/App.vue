<script >
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue';
import Main from './components/Main.vue'
export default {
  components: {
    Header,
    Main
  }
}
</script>

<template>
  <Header></Header>
  <Main></Main>
</template>

<style lang="scss" scoped>
@use './style/general.scss';
</style>
