<template>
  <div id="app">
    <h1>POSTS</h1>
    <hr />
    <button class="button_get" type="button" @click="getPosts">GET POSTS</button>
    <ul>
      <li v-for="post of posts" :key="post.id">{{post.title}}
        <button @click="removePost(post.id)">&times;</button>
      </li>
    </ul>
  
  </div>
</template>

<script>

import axios from 'axios'

export default {
  name: 'App',
  data(){
    return {
      posts: []
    }
  },
  methods: {
    getPosts() {
        axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then(response => (this.posts = response.data))
    },
    removePost(id) {
      console.log(id)
      this.posts = this.posts.filter(p => p.id !== id)
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  ul {
    padding: 0;
  }
  li {
    list-style: none;
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin: 1rem 20%;

    button {
      background-color: rgb(255, 73, 73);
      border: none;
      border-radius: 0.3rem;
    }
  }
  .button_get {
    width: 30%;
    height: 2.5rem;
    background-color: rgb(94, 212, 94);
    border: none;
    border-radius: 0.3rem;
  }
}
</style>
