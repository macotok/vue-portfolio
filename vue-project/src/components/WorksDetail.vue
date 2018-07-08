<template>
  <div>
    <article>
      <h1 v-cloak>{{ filterData.title }}</h1>
      <div v-for="(p, index) in filterData.picture" :key='index' v-if="p.id === 1">
        <img :src="p.path">
      </div>
      <p v-cloak>{{ filterData.text }}</p>
      <p v-cloak>制作年: {{ filterData.year }}</p>
      <p v-cloak>{{ filterData.role }}</p>
      <p v-cloak><a :href="filterData.url" tartget="_blank">{{ filterData.urlTitle}}</a></p>
      <div v-for="(p, index) in filterData.picture" :key='index' v-if="p.id !== 1">
        <img :src="p.path">
      </div>
    </article>
  </div>
</template>

<script>
export default {
  title: '',
  description: '',
  props: ['data'],
  computed: {
    filterData() {
      const url = `${window.location.protocol}//${window.location.host}/works/`;
      const matchData = this.data.filter((item) => {
        if (item.slug === window.location.href.replace(url, '')) {
          return true;
        }
        return false;
      });
      return matchData[0];
    },
  },
  mounted() {
    document.title = `${this.filterData.title} - macotok portfolio`;

    const meta = document.getElementsByTagName('meta');
    for (let i = 0; i < meta.length; i += 1) {
      if (meta[i].name.toLowerCase() === 'description') {
        meta[i].content = `${this.filterData.title}について`;
      }
    }
  },
};
</script>
