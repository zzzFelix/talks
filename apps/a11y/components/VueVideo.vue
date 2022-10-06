<template>
    <article>
        <img :src="stillSrc" alt="Screencast of YouTube displaying the use of captions for previews" class="vue-video">
        <video v-click class="vue-video" ref="video">
            <source :src="src" type="video/mp4">
        </video>
    </article>
</template>

<script setup lang="ts">
import { ref, VNodeRef, watch } from 'vue';

const video: VNodeRef = ref(null)

const props = defineProps({
    src: {
        type: String,
        required: true
    },
    stillSrc: {
        type: String,
        required: true
    },
    clicks: {
        type: Number,
        required: true
    }
})

watch(() => props.clicks, (newValue: number) => {
    if (newValue === 1) {
        video?.value?.play();
    } else {
        video?.value?.pause();
    }
});
</script>

<style>
article {
    display: grid;
    grid-template-areas: video;
}

.vue-video {
    height: 22rem;
    grid-area: video;
}
</style>