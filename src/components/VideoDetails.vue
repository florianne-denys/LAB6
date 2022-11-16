<script setup>
    import {ref, onMounted} from 'vue';
    let username = ref("")
    let description = ref("")

    //onmounted
    onMounted(() => {
        const apiUrl = "https://app.fakejson.com/q/sHND3IsF?token=YVDNVYq8PQx-CCMscIJrwQ"
        fetch(apiUrl)
            .then(res => res.json())
            .then(data => {
                username.value = data.videos[0].username
                description.value = data.videos[0].description
            })
    })
</script>

<template>
  <div>
    <h3>{{ username }}</h3>
    <p>{{ description }}</p>
  </div>
</template>

<style scoped>
    div{
        padding: 1rem;
    }
</style>