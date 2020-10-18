<template>
<div>
    <v-list-item class="list-custom-item" @click="onVideoSelect">
        <v-img alt="video" max-width="150" height="100" :src="thumbnailItem"></v-img>
        <v-list-item-content>
            <v-list-item-title>{{ video.snippet.title }}</v-list-item-title>
        </v-list-item-content>
    </v-list-item>
    <v-divider class="list-custom-divider"></v-divider>
</div>
</template>

<script>
export default {
    name: "VideoListItem",
    props: {
        video: Object,
    },
    methods: {
        onVideoSelect() {
            this.$emit("video-selected", this.video);
        },
    },
    computed: {
        thumbnailItem() {
            return this.video.snippet.thumbnails.default.url;
        },
    },
};
</script>

<style scoped>
.list-custom-divider {
    margin: 20px 0px;
}

.list-custom-item:hover {
    background-color: #eee;
    cursor: pointer;
}
</style>
