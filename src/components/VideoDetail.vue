<template>
<div v-if="video" class="details">
    <div>
        <div class="videoContainer">
            <iframe class="videoPlayer" :src="videoUrl"/>
        </div>
        <h4>{{ video.snippet.title }}</h4>
        <p>{{  video.snippet.description  }}</p>
    </div>
</div>
<div v-else class="nullDetails">
    <h5>Sad trombone! you haven't found a video yet?!?!</h5>
</div>
    
</template>

<script>
export default {
    name: 'VideoDetail',
    props: ['video'],
    computed: {
        videoUrl() {
            const { videoId } = this.video.id;
            return `https://www.youtube.com/embed/${videoId}`;
        }
    }
    
}
</script>

<style scoped>
.details{
    margin: 5rem;
}

.nullDetails{
    width: 66vw;
    height: 100vh;
    background: url(../img/sad.gif) center center no-repeat;
    background-color: #b3ebe1;
    text-align: center;
}
.nullDetails h5{
    margin-top: 10%;
}
.videoContainer{
    position: relative;
    width: 100%;
    padding-bottom:56.25%;
    height: 0;
}
.videoPlayer {
    border: none;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
h4{
    margin-top: 2rem;
}

</style>