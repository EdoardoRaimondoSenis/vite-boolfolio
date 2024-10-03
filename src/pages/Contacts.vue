<script>

import axios from 'axios';
import { store } from '../store/store.js';

    export default {
        name: 'Contacts',
        data() {
            return {
                name: '',
                email: '',
                message: '',
                errors:{
                    name:[],
                    email:[],
                    message:[]
                },
            }
        },
        methods: {
            getContacts() {
                const data = {
                    name: this.name,
                    email: this.email,
                    message: this.message
                }

                axios.post(store.apiUrl + 'send-mail', data)
                    .then(response => {
                        if (!response.data.success) {
                            this.errors = response.data.errors;
                        } else {
                            this.errors = {
                                name: [],
                                email: [],
                                message: []
                            }
                        }
                    })
                    .catch(error => {
                        console.log(error.message);
                    })

            }

        },
    };

</script>

<template>

    <div class="container">
        <h1>Contatti</h1>
        <form action="#" @submit.prevent="getContacts">
            <div>
                <label for="name">Nome</label><br>
                <input v-model="name" type="text" id="name" placeholder="Nome">
                <p class="error">{{ errors.name?.toString() }}</p>
            </div>
            <div>
                <label for="email">Email</label><br>
                <input v-model="email" type="email" id="email" placeholder="Email">
                <p class="error">{{ errors.email?.toString() }}</p>
            </div>
            <div>
                <label for="message">Messaggio</label><br>
                <textarea v-model="message" id="message" placeholder="Messaggio"></textarea>
                <p class="error">{{ errors.message?.toString() }}</p>
            </div>
            <div>
                <button class="btn btn-primary" type="submit">Invia</button>
                <button class="btn btn-warning" type="reset">Annulla</button>
            </div>
        </form>
    </div>

</template>

<style lang="scss">

.container {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

button {
    margin-right: 1rem;
}


</style>