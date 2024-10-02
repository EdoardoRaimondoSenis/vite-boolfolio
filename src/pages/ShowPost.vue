<script>
  import axios from 'axios';
  import { store } from '../store/store.js';
  
  export default {
    name: 'showpost',
    props: ['id'],
    data() {
      return {
        posts: null,
      };
    },
    methods: {
      getProjectDetails() {
        axios.get(store.apiUrl + 'posts/' + this.id).then(response => {
          this.posts = response.data.id;
          console.log(this.posts);
          
        })
      }
    },
    mounted() {
      this.getProjectDetails();
    }
  };
  </script>

<template>
    <div class="container">
        <div v-if="posts">
            <h1>{{ posts.title }}</h1> 
            <p>{{ posts.argument }}</p> 
            <p>{{ posts.collaborators }}</p>
        </div>
        <div v-else>
            <div class="loader"></div>
        </div>
    </div>
</template>

<style lang="scss">

.loader {
  height: 35px;
  aspect-ratio: 1;
  border: 3px solid #fff;
  animation: l4 2s infinite;
}
@keyframes l4 {
  0%  {aspect-ratio:1;border-radius:50px}
  25% {aspect-ratio:2;border-radius:50px} 
  50% {aspect-ratio:2;border-radius:0}  
  75% {aspect-ratio:1;border-radius:0} 
  100%{aspect-ratio:1;border-radius:50px}
}

</style>