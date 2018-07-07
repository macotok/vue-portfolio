<template>
  <div class="wrapper">
    <main>
      <h1>作品ページ</h1>
      <router-view v-bind:data="myData"></router-view>
    </main>
  </div>
</template>

<script>
import myData from '../../../static/data.json';

export default {
  data() {
    return {
      myData,
    };
  },
};
</script>
