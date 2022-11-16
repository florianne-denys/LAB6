<script setup>
    //imports
    import {reactive, ref} from 'vue';
    let title = ref("Hello vue!")
    //data
    const comments = reactive([
        {
            name: "John",
            comment: "Hello"
        },
        {
            name: "Jane",
            comment: "Hi"
        }
    ])
    //functions
    const addComment = () => {
        comments.push({
            name: "New user",
            comment: title.value
        })
    }
</script>

<template>
  <div>
    <h1>{{ title }}</h1>
    <ul>
      <li v-for="comment in comments" :key="comment.name">
        <h3>{{ comment.name }}</h3>
        <p>{{ comment.comment }}</p>
      </li>
    </ul>

    <input type="text" v-model="title">
    <button @click.prevent="addComment">Add Comment</button>
  </div>
</template>

<style scoped>

</style>