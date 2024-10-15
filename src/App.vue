<script setup>
import { ref } from 'vue';
import navBar from './components/nav-bar.vue';
import PageViewer from './components/page-viewer.vue';

const pages = [
  {
    pageTitle: 'Home page', content: 'This is the home content',
    link: {
      text: 'Home', url: 'index.html'
    }
  },
  {
    pageTitle: 'About page', content: 'This is the about content',
    link: {
      text: 'About', url: 'about.html'
    }
  },
  {
    pageTitle: 'Contact page', content: 'This is the contact content',
    link: {
      text: 'Contact', url: 'contact.html'
    }
  }
]

const activePage = ref(0)
const changePage = (index) => {
  activePage.value = index
}

const theme = ref('light')
const changeTheme = () => {
  theme.value = theme.value == 'light' ? 'dark' : 'light'
}

</script>

<template>
  <nav-bar :pages="pages" :activePage="activePage" :theme="theme" :changePage="changePage"
    :changeTheme="changeTheme"></nav-bar>

  <page-viewer :page="pages[activePage]"></page-viewer>
</template>
