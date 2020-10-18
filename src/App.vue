<template>
<v-main>
    <v-container>
        <v-row class="w-100">
            <SearchBar @term-change="onTermChange" />
        </v-row>
        <v-row>
            <v-col sm="12" md="7">
                <VideoDetails v-if="this.selectedVideo" :selectedVideo="this.selectedVideo"></VideoDetails>
            </v-col>
            <v-col sm="12" md="5">
                <VideoList :videos="videos" @video-selected="onVideoSelected"></VideoList>
            </v-col>
        </v-row>
    </v-container>
</v-main>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetails from "./components/VideoDetails";

export default {
    name: "App",
    components: {
        SearchBar,
        VideoList,
        VideoDetails,
    },
    // eslint-disable-next-line space-before-function-paren
    data() {
        return {
            videos: [],
            selectedVideo: null,
        };
    },
    methods: {
        // eslint-disable-next-line space-before-function-paren
        onTermChange(term) {
            axios
                .get("https://www.googleapis.com/youtube/v3/search", {
                    params: {
                        key: process.env.VUE_APP_API_KEY,
                        type: "video",
                        part: "snippet",
                        q: term,
                    },
                })
                .then((response) => {
                    console.log("RE", response.data.items);
                    this.videos = response.data.items;
                });
        },
        onVideoSelected(video) {
            this.selectedVideo = video;
        },
    },
};
</script>
