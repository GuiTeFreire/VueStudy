<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    pages: Array,
    activePage: Number,
    theme: String,
    changePage: Function,
    changeTheme: Function,
})
</script>

<template>
    <nav :class="[`navbar-${props.theme}`, `bg-${props.theme}`, 'navbar', 'navbar-expand-lg']">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">My Vue</a>

            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li v-for="(page, index) in props.pages" :key="index" class="nav-item">
                    <a class="nav-link" :class="{ active: props.activePage == index }" aria-current="page"
                        :href="page.link.url" :title="`This link goes to the ${page.link.text} page`"
                        @click.prevent="props.changePage(index)">
                        {{ page.link.text }}
                    </a>
                </li>
            </ul>

            <form class="d-flex">
                <button class="btn btn-primary" @click.prevent="props.changeTheme()">
                    Toggle Navbar
                </button>
            </form>
        </div>
    </nav>
</template>