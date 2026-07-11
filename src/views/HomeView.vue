<template>
    <main class="container text-white">
        <div class="pt-4 mb-8 relative">
            <input type="text" v-model="searchKeyword" class="w-full py-2 px-1 bg-transparent border-b border-gray-400
            focus:outline-0 focus:border-secondary focus:shadow-lg" placeholder="搜索">
        </div>
    </main>
</template>

<script setup>
import { ref } from 'vue';

const searchKeyword = ref("")
</script>

<style lang="scss" scoped>

</style>