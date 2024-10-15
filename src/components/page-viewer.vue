<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    page: Object
})

</script>

<template>
    <div class="container">
        <h1>{{ props.page.pageTitle }}</h1>
        <p>{{ props.page.content }}</p>
    </div>
</template>