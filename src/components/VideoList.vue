<template>
    <ul>
        <VideoListItem 
            v-for="video in videos"
            :video="video"
            :key="video.etag"
            @videoSelect="onVideoSelect"
        >
        </VideoListItem>
    </ul>
    <!-- <ul v-else class="nullList">
        <img src="../img/will-smith-empty.gif" alt="image of Will Smith looking at an empty living room" />
    </ul> -->
</template>

<script>
import VideoListItem from './VideoListItem';

export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: ['videos'],
    methods: {
        onVideoSelect(video) {
            this.$emit('videoSelect', video);
        }
    }
};
</script>

<style scoped>
    ul {
        grid-column-start: 2;
        list-style: none;
        background-color: #f6fffd;
        padding: 3rem;
    }
    
    .nullList{
        /* background: url(../img/sad.gif) no-repeat center center fixed; 
        -webkit-background-size: cover;
        -moz-background-size: cover;
        -o-background-size: cover;
        background-size: cover; */
    }

</style>