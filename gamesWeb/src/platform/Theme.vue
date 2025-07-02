<template>
    <div :class="themeClass">
        <slot />
    </div>
</template>

<script setup>
import { ref, watch, provide } from 'vue'

const theme = ref(localStorage.getItem('theme') || 'light')

const setTheme = (newTheme) => {
    theme.value = newTheme
    localStorage.setItem('theme', newTheme)
    document.documentElement.setAttribute('data-theme', newTheme)
}

watch(theme, (newTheme) => {
    document.documentElement.setAttribute('data-theme', newTheme)
})

provide('theme', theme)
provide('setTheme', setTheme)

const themeClass = computed(() => `theme-${theme.value}`)

// 初始化时设置主题
document.documentElement.setAttribute('data-theme', theme.value)
</script>

<style scoped>
.theme-light {
    /* 亮色主题样式 */
    background: #fff;
    color: #222;
}

.theme-dark {
    /* 暗色主题样式 */
    background: #222;
    color: #fff;
}
</style>