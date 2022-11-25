<script setup>
  //import VideoPlayer.vue
  import VideoPlayer from './components/VideoPlayer.vue'
  //import VideoDetails.vue
  import VideoDetails from './components/VideoDetails.vue'
  //import Comments.vue
  import Comments from './components/Comments.vue'

</script>

<template>
  <div class="app">
    <VideoPlayer/>
    <VideoDetails/>
    <Comments/>
  </div>
</template>

<style scoped>
  .app{
    display: grid;
    grid-template-columns: 8fr 4fr;
  }
</style>
