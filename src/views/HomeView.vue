<template>
    <main class="container text-white">
        <div class="pt-4 mb-8 relative">
            <input type="text" v-model="searchKeyword"
            @input="getSearchResults"
                class="w-full py-2 px-1 bg-transparent border-b border-gray-400 focus:outline-0 focus:border-secondary focus:shadow-lg"
                placeholder="搜索" />
        </div>
    </main>
</template>

<script setup>
import { ref } from "vue";
const mapApiKey = "";

const searchKeyword = ref("");
const queryTimeout = ref(null);
const apiSearchResults = ref(null)

const getSearchResults = () => {
    clearTimeout(queryTimeout.value)
    queryTimeout.value = setTimeout(async () => {
        if (searchKeyword.value !== "") {
            const response = await fetch(
                `https://api.mapbox.com/geocoding/v5/mapbox.places/${searchKeyword.value}.json?access_token=${mapApiKey}&type=place`,
            );
            const data = await response.json();
            apiSearchResults.value = data.features
            console.log(apiSearchResults.value)
            return

        }
        apiSearchResults.value = null
    }, 300);
};
</script>

<style lang="scss" scoped></style>
