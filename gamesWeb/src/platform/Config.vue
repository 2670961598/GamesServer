<script setup>
import { reactive, provide, inject } from 'vue'

// 定义平台配置
const platformConfig = reactive({
    name: 'web', // 可选: 'web', 'mobile', 'desktop' 等
    version: '1.0.0',
    features: {
        chat: true,
        leaderboard: false,
        notifications: true,
    }
})

// 提供全局配置
provide('platformConfig', platformConfig)
</script>

<template>
    <slot />
</template>