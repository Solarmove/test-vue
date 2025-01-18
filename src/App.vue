<script setup lang="ts">
import { onBeforeMount, onMounted, ref } from 'vue'
import { RouterView } from 'vue-router'
import { useWebAppTheme, useWebAppViewport } from 'vue-tg'
const { disableVerticalSwipes, expand } = useWebAppViewport()
const { setBackgroundColor, setHeaderColor } = useWebAppTheme()
const isLoading = ref(true)


let tg = window.Telegram.WebApp

onBeforeMount(() => {
    setHeaderColor(tg.themeParams.header_bg_color!)
    setBackgroundColor(tg.themeParams.bg_color!)
    disableVerticalSwipes()
    expand()
})

onMounted(async () => {
    isLoading.value = false
    tg.ready
})
</script>

<template>
    <div class="main-container">
        <RouterView />
    </div>
</template>

<style scoped>
.main-container {
    overflow: hidden;
}
</style>
