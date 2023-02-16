<template>
    <video height="100px" class="vue-video" v-if="!videoPlays" @click="videoPlays = true">
        <source :src="src" type="video/mp4">
    </video>

    <video autoplay height="100px" class="vue-video" v-if="videoPlays" @click="videoPlays = false">
        <source :src="src" type="video/mp4">
    </video>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const videoPlays = ref(false);

defineProps({
    src: {
        type: String,
        required: true
    }
})
</script>

<style>
.vue-video {
    height: 22rem;
}
</style>