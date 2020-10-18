<template>
<v-list>
    <VideoListItem v-for="video in videos" :video="video" :key="video.etag" @video-selected="onVideoSelect"></VideoListItem>
</v-list>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
    name: "VideoList",
    components: {
        VideoListItem,
    },
    props: {
        videos: Array,
    },
    methods: {
        onVideoSelect(video) {
            this.$emit("video-selected", video);
        },
    },
};
</script>

<style scoped></style>
