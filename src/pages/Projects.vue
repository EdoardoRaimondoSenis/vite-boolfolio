<script>

import axios from 'axios';
import { store } from '../store/store.js';
export default {
    name: 'Projects',
    data() {
        return {
            posts: [],
            technologies: [],
            types: [],
        };
    },

    methods: {
        getApiPosts() {
            axios.get(store.apiUrl + 'posts').then(response => {
                this.posts = response.data.posts;
                console.log(this.posts);
            })
        },

        getApiTechnologies() {
            axios.get(store.apiUrl + 'technologies').then(response => {
                this.technologies = response.data.technologies;
                console.log(this.posts);
            })
        },

        getApiTypes() {
            axios.get(store.apiUrl + 'types').then(response => {
                this.types = response.data.types;
                console.log(this.posts);
            })
        },
        
    },

    mounted() {
        this.getApiPosts();
        this.getApiTechnologies();
        this.getApiTypes();
    }
};
</script>


<template>
    <div>
        <h1>Projects</h1>
        <ul>
            <h2>Titoli Posts</h2>
            <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
        </ul>
        <ul>
            <h2>Tecnologie</h2>
            <li v-for="technology in technologies" :key="technology.id">{{ technology.name }}</li>
        </ul>
        <ul>
            <h2>Tipi</h2>
            <li v-for="type in types" :key="type.id">{{ type.name }}</li>
        </ul>
    </div>
</template>


<style lang="scss">

</style>