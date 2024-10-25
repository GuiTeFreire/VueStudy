<template>
  <navbar :pages="pages" :activePage="activePage" :nav-link-click="(index) => activePage = index" />

  <page-viewer :page="pages[activePage]" />
</template>

<script>
import Navbar from './components/NavigationBar.vue';
import PageViewer from './components/PageViewer.vue';

export default {
  components: {
    PageViewer,
    Navbar,
  },
  created() {
    this.getPages();
  },
  data() {
    return {
      activePage: 0,
      pages: []
    }
  },
  methods: {
    async getPages() {
      let response = await fetch('pages.json');
      let data = await response.json();

      this.pages = data;
    }
  }
}

</script>