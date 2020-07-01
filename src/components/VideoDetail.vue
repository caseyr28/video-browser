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
    <!-- <img src="../img/sad.gif" alt="image of Will Ferrel crying, drinking wine" /> -->
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
    background: url(../img/sad.gif) no-repeat center center fixed; 
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
    text-align: center;
}
/* .nullDetails:after{
    content: ' ';
    display: block;
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    opacity: 0.6;
    background-image: url(../img/sad.gif);
    background-repeat: no-repeat;
    background-position: 50% 0;
    -ms-background-size: contain;
    -o-background-size: contain;
    -moz-background-size: contain;
    -webkit-background-size: contain;
    background-size: contain;
} */
.nullDetails h5{
    margin-top: 10%;
    margin-bottom: 1px;
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
h5{
    margin-top: 2rem;
    color: white;
}

</style>