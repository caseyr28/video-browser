<template>
    <div class='container'>
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div class="mainLayout">
            <VideoDetail :video="selectedVideo"></VideoDetail>
            <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';
const API_KEY = "AIzaSyBRVfgfY0IZq6wFHsB2S56oHQxYjuiVnkw";

export default {
    name: 'App',
    components: {
        SearchBar, 
        VideoList, 
        VideoDetail
    },
    data() {
        return { 
            videos: [], 
            selectedVideo: null 
        };
    },
    methods: {
        onVideoSelect(video) {
            this.selectedVideo = video;
        },
        onTermChange(searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => 
                {this.videos = response.data.items;
                });
        }
    }
}
</script>

<style>
.mainLayout{
    display: grid;
    grid-template-columns: 66% 1fr;
}
</style>