<template>
  <nav-view />
  <router-view/>
</template>


<script>
import NavView from '@/components/NavView.vue';

export default {
  components: {
    NavView
  },
};
</script>
<style>
body{
  background: #f2f2f2;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  max-width: 600px;
  margin: 0  auto;
  color: #555;
}


</style>
