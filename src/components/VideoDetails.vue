<template>
<v-card class="mx-auto">
    <iframe :src="embededUrl" width="100%" height="344px" />

    <v-card-title>
        {{ selectedVideo.snippet.title }}
    </v-card-title>

    <v-card-subtitle>
        {{ selectedVideo.snippet.description }}
    </v-card-subtitle>
</v-card>
</template>

<script>
export default {
    name: "VideoDetails",
    props: {
        selectedVideo: Object,
    },
    computed: {
        embededUrl() {
            const {
                videoId
            } = this.selectedVideo.id;
            return `https://www.youtube.com/embed/${videoId}`;
        },
    },
};
</script>

<style scoped></style>
