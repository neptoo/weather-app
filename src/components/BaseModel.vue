<template>
    <div v-show="modalActive" class="absolute w-full bg-black-30 h-screen top-0 left-0 flex justify-center px-8">
        <div v-if="modalActive" class="p-6 bg-white self-start mt-32 max-screen-md rounded-md">
            <slot></slot>
            <button class="text-white bg-primary py-2 px-6 mt-8">关闭</button>
        </div>
    </div>
</template>

<script setup>
defineProps({
    modalActive: {
        type: Boolean,
        default: false
    }
})

</script>

<style lang="scss" scoped>

</style>