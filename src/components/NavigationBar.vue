<template>
  <header class="sticky top-0 bg-primary shadow-lg">
    <nav
      class="container flex flex-col sm:flex-row items-center gap-4 text-white py-6"
    >
      <RouterLink :to="{ name: 'home' }">
        <div class="flex items-center gap-3">
          <i class="fa-solid fa-sun text-2xl"></i>
          <p class="text-2xl">当地天气</p>
        </div>
      </RouterLink>
      <div class="flex gap-3 flex-1 justify-end">
        <i
          class="fa-solid fa-circle-info text-xl hover:text-secondary duration-150 cursor-pointer"
          @click="toggleModal"
        ></i>
        <i
          class="fa-solid fa-plus text-xl hover:text-secondary duration-150 cursor-pointer"
        ></i>
      </div>
      <BaseModel :modalActive="modalActive" @close-modal="toggleModal">
        <div class="text-black">
          <h1 class="text-2xl mb-1">关于本站：</h1>
          <p class="mb-4">可查看所选城市的当前天气和未来天气</p>
          <h2 class="text-2xl">使用方法：</h2>
          <ol class="list-decimal list-inside mb-4">
            <li>在搜索框中输入城市名称，即可搜索对应的城市</li>
            <li>在搜索结果中选择一个城市，可以直接打开该城市的天气页面</li>
            <li>
              点击右上角的“+”图标来添加和保存城市，之后可以在主页中查看该城市
            </li>
          </ol>

          <h2 class="text-2xl">移除城市</h2>
          <p>
            如果你不再需要关注某个城市，请在主页中选中该城市，然后在页面底部会有删除该城市的选项
          </p>
        </div>
      </BaseModel>
    </nav>
  </header>
</template>

<script setup>
import { ref } from "vue";
import { RouterLink } from "vue-router";
import BaseModel from "./BaseModel.vue";

const modalActive = ref(false);
const toggleModal = () => {
  modalActive.value = !modalActive.value;
};
</script>

<style lang="scss" scoped></style>
