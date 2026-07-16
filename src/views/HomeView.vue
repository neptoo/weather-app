<template>
    <main class="container text-white">
        <div class="pt-4 mb-8 relative">
            <input type="text" v-model="searchKeyword"
            @input="getSearchResults"
                class="w-full py-2 px-1 bg-transparent border-b border-gray-400 focus:outline-0 focus:border-secondary focus:shadow-lg"
                placeholder="搜索" />

            <ul v-if="apiSearchResults" class="absolute bg-highlight text-white w-full py-2 px-1 rounded-xl shadow-md top-[60px]">
                <p v-if="searchError">出错了，请稍后重试</p>
                <p v-if="!searchError && apiSearchResults.length === 0">未查找到相关结果，请更换关键词重新搜索</p>
                <template v-else>
                    <li v-for="searchResult in apiSearchResults" :key="searchResult.id"
                     class="py-2 cursor-pointer">{{ searchResult.place_name }}</li>
                </template>
            </ul>
        </div>
    </main>
</template>

<script setup>
import { ref } from "vue";
// https://docs.mapbox.com/api/search/geocoding/
// 替换成你的API token
const mapApiKey = "";

const searchKeyword = ref("");
const queryTimeout = ref(null);
const apiSearchResults = ref(null)
const searchError = ref(false)

const getSearchResults = () => {
    clearTimeout(queryTimeout.value)
    queryTimeout.value = setTimeout(async () => {
        if (searchKeyword.value !== "") {
            try {
                      const response = await fetch(
                `https://api.mapbox.com/geocoding/v5/mapbox.places/${searchKeyword.value}.json?access_token=${mapApiKey}&type=place`,
            );
            const data = await response.json();
            apiSearchResults.value = data.features
            console.log(apiSearchResults.value)      
            } catch (error) {
                searchError.value = true
            }
            return

        }
        apiSearchResults.value = null
    }, 300);
};
</script>

<style lang="scss" scoped></style>
