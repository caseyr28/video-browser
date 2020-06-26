<template>
    <li @click="onVideoSelect">
      <img :src="thumbnailUrl"/>
      <!-- <h6></h6> -->
      <h6>{{ video.snippet.title }}</h6>
    </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: ['video'] ,
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
    videoTitle() {
      return this.video.snippet.title;
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video);
    }
  } 
};
</script>
<style scoped>
  li {
    cursor: pointer;
    padding: 2.0rem;
    border: 1px #d8fff8 solid;
    border-radius: 4px;
    display: flex;
    justify-self: end;
    }
  li:hover {
    background-color: #d8fff8;
  }
  li img {
    padding: 2px 20px 0 0;
  }
</style>

