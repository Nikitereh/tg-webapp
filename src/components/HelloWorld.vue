<script setup lang="ts">
const tg = window.Telegram.WebApp;
import {ref, onMounted} from 'vue'

defineProps<{ msg: string }>()

const isReady = ref(false);
const close = () => {
    tg.close();
}

onMounted(async () => {
    await tg.ready();
    isReady.value = true;
})
</script>

<template>
    <h1>{{ msg }}</h1>
    <p v-if="isReady">ready</p>
    <button @click="close">close</button>
</template>
