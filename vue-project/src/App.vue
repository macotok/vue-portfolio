<template>
  <div id="app">
    <div class="header-router" id="sticky">
      <header>
        <h1 class="site-title"><router-link to="/">macotok portfolio</router-link></h1>
      </header>
      <hnav></hnav>
    </div>
    <transition name="fade">
      <router-view :data="myData"></router-view>
    </transition>
  </div>
</template>

<script>
import HeaderNav from '@/components/parts/NavHeader';
import myData from '../static/data.json';

export default {
  name: 'App',
  components: {
    hnav: HeaderNav,
  },
  data() {
    return {
      myData,
    };
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
