<script setup>
    import {ref, onMounted, reactive} from 'vue';
    import 'animate.css';

    let videos = reactive({data: []});
    let videoSrc =ref("");
    let counter = ref(0);
    let animation = ref("");

    //onMounted
    onMounted(() => {
        console.log("mounted")
        const apiUrl = "https://app.fakejson.com/q/sHND3IsF?token=YVDNVYq8PQx-CCMscIJrwQ"
        fetch(apiUrl)
            .then(res => res.json())
            .then(data => {
                videos.data = data.videos;
                videoSrc.value = data.videos[0].video
            })
    })

    const nextVideo = ( ) => {
        animation.value = "animate__fadeOutUp";
        setTimeout(() => {
            videoSrc.value = videos.data[counter.value].video;
            animation.value = "animate__fadeInUp";
        }, 500)
        counter.value++;
        videoSrc.value = videos.data[counter.value].video
    }
</script>

<template>
  <div class="blur">
    <div class="controls">
        <a @click.prevent="nextVideo" href="#">⬇️</a>
    </div>
    <video :src="videoSrc" :class="animation" class="animate__animated" controls autoplay muted></video>
  </div>

</template>

<style scoped>
    video{
        max-width: 100%;
        max-height: 100vh;
    }
    .blur{
        background-image: url(../assets/blur.jpg);
        background-size: cover;
        text-align: center;
        position: relative;
    }
    .controls{
        position: absolute;
        top: 0;
        right: 0;
        height: 100%;
        display: flex;
        align-items: center;
    }
    .controls a{
        color: white;
        font-size: 2rem;
        padding: 1rem;
        text-decoration: none;
    }
</style>