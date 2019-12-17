<template>
  <li class="list-group-item media">
    <img class="mr-3" :src="thumbnailsUrl" alt />
    <div class="media-body">{{video.snippet.title}}</div>
  </li>
</template>
<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    thumbnailsUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  }
};
</script>
<style scoped>
li {
  display: flex;
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
</style>
