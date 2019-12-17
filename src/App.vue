<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList @videoSelect="onVideoSelect" :videos="videos" />
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
const API_KEY = process.env.VUE_APP_API_KEY;
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      videos: []
    };
  },
  components: {
    SearchBar,
    VideoList
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(response => {
          this.videos = response.data.items;
        });
    },
    onVideoSelect(video) {
      console.log(video);
    }
  }
};
</script>

<style></style>
