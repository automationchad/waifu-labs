<template>
    <div class="relative">
        <Navbar v-if="route.path !== '/login' && route.path !== '/signup'" class="sticky z-50 top-0 w-full"/>
        <NuxtPage class=""/>
    </div>
</template>

<script setup>
const route = useRoute();
</script>

<style>

* {
    box-sizing: border-box;
}

</style>