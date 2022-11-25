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
    <div class="info">
      <VideoDetails/>
      <Comments/>
    </div>
  </div>
</template>

<style scoped>
  .app{
    display: grid;
    grid-template-columns: 8fr 4fr;
  }
  .info{
    display: flex 20% 80%;
    flex-direction: column;
    padding: 1rem;
  }
</style>
