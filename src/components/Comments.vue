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
    <div class="comments">
      <ul >
      <li v-for="comment in comments" :key="comment.name">
        <h3>{{ comment.name }}</h3>
        <p>{{ comment.comment }}</p>
      </li>
    </ul>
    </div>
    
    <div class="input">
      <input type="text" v-model="title">
      <button @click.prevent="addComment">Add Comment</button>
    </div>
  </div>
</template>

<style scoped>
    .comments{
      width: 100;
      height: 350px;
      background-color: rgb(231, 231, 231);
      overflow: scroll;
    }
    .comments ul{
      list-style: none;
      padding: 10px;
    }
    .input{
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: fixed;
      bottom: 10px;
      width: 30%;
    }
    .input input{
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      width: 65%;
    }
    .input button{
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      background-color: #fff;
      cursor: pointer;
    }
  
</style>