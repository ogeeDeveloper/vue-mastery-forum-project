<script setup lang="ts">
import forumData from "../data.json"

const threads = forumData.threads
const posts = forumData.posts
const users = forumData.users

// Find post by Id
const findPostById = postId => {
  return posts.find(post => post.id == postId)
}

const findUserById = userId =>{
  return users.find(post => post.id === userId)
}

</script>

<template>
<h1>Hello from the home-page</h1>
  <div v-for="thread in threads" :key="thread.id">
    <h2>{{thread.title}}</h2>
    <div v-for="postId in thread.posts" key="postId">
      <!--for fetching of post-->
      <p>{{findUserById(findPostById(postId).userId).name}}</p>
      <!--for fetching of post-->
      <p>{{ findPostById(postId).text}}</p>
    </div>
  </div>
</template>

<style scoped>

</style>