<script>
  import axios from 'axios';
  import { store } from '../store/store.js';
  
  export default {
    name: 'showpost',
    props: ['id'],
    data() {
      return {
        post: null,
      };
    },
    methods: {
      getProjectDetails() {
        console.log('ID del post:', this.id);
        axios.get(store.apiUrl + 'posts/' + this.id).then(response => {
          this.post = response.data;
          console.log(this.post);
          
        });
      }
    },
    mounted() {
      this.getProjectDetails();
    }
  };
  </script>

<template>
    <div class="container">
        <div v-for="post in posts">
            <h1>Dettagli di: {{ post.title }}</h1>
            <p>{{ post.argument }}</p>
            <h3>{{ post.collaborators }}</h3>
        </div>
    </div>
</template>

<style lang="scss">

</style>