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

            })
        },

        getApiTypes() {
            axios.get(store.apiUrl + 'types').then(response => {
                this.types = response.data.types;
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
    <div class="container ml-5 mt-3 mb-2">
        <h1>Projects</h1>
    </div>
    <div class="container">
        <ul>
            <h2>Id Posts</h2>
            <li v-for="post in posts" :key="post.id">{{ post.id }}</li>
        </ul>
        <ul>
            <h2>Titoli Posts</h2>
            <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
        </ul>
        <ul class="uls">
            <h2>Tecnologie</h2>
            <li v-for="technology in technologies" :key="technology.id">{{ technology.name }}</li>
        </ul>
        <ul class="uls">
            <h2>Tipi</h2>
            <li v-for="type in types" :key="type.id">{{ type.name }}</li>
        </ul>
        <ul class="router">
            <li v-for="post in posts" :key="post.id">
                <router-link :to="{ name: 'showpost', params: { id: post.id } }">Vedi Dettagli</router-link>
            </li>
        </ul>
    </div>
</template>


<style lang="scss">

.container {
    display: flex;
}

.router {
    list-style: none;
    margin-top: 3rem;
    line-height: 1.55rem;
    a {
        color: crimson;
    }
}

</style>