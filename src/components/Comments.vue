<script setup>
    //imports
    import {reactive, ref, onMounted} from 'vue';
    let commentInput = ref("");
    let commentData = reactive({ comments: [] });
    //comments ophalen
    onMounted(() => {
        const api_url = "https://lab5-p379.onrender.com/api/v1/messages/";
        fetch(api_url)
            .then(response => response.json())
            .then(data => {
                commentData.comments = data;
                console.log(commentData.comments);
            });
    });
    //comment toevoegen
    const addComment = () => {
    let data = {
        user: "Florianne",
        text: commentInput.value
    };
    fetch("https://lab5-p379.onrender.com/api/v1/messages/", {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(data)
    })
        .then(response => response.json())
        .then(data => {
            console.log('Success:', data);
            commentData.comments.push({
                commentId: data.id,
                user: data.user,
                text: data.text
            })
        })
        .catch((error) => {
            console.error('Error:', error);
        });
}
</script>

<template>
  <div>
    <h1>Comments</h1>
    <div class="comments">
      <ul >
      <li v-for="comment in commentData.comments" :key="commentData.comments.id">
        <h3>{{ comment.user }}</h3>
        <p>{{ comment.text }}</p>
      </li>
    </ul>
    </div>
    
    <div class="input">
      <input type="text" v-model="commentInput">
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