<template>
  <div>
    <h1>作品紹介</h1>
    <article v-for="(d, index) in data" :key='index'>
      <div v-for="(p, index) in d.picture" :key='index' v-if="p.id === '1'">
        <router-link :to="'/works/' + d.slug"><img :src="p.path"></router-link>
      </div>
      <div>
        <h1 v-cloak><router-link :to="'/works/' + d.slug">{{ d.title }}</router-link></h1>
        <p class="work-description" v-cloak>{{ d.text }}</p>
        <p class="work-year" v-cloak>制作年: {{ d.year }}</p>
      </div>
    </article>
  </div>
</template>

<script>
export default {
  title: '',
  description: '',
  props: ['data'],
};
</script>
