<template>
    <div class="container">
        <h1>Novo usuário</h1>
        <form @submit.prevent="sendFormNewUser" action="">
            <div class="form-group">
                <label for="name">Nome</label>
                <input type="text" class="form-control" v-model="user.name">
            </div>
            <div class="form-group">
                <label for="email">E-mail</label>
                <input type="text" class="form-control" v-model="user.email">
            </div>
            <div class="form-group">
                <label for="password">Senha</label>
                <input type="password" class="form-control" v-model="user.password">
            </div>
            <button class="btn btn-primary" type="submit">Salvar</button>
        </form>
    </div>
</template>

<script>

import axios from 'axios';

export default {
    data: function() {
        return {
            user: {
                name: '',
                email: '',
                password: ''
            }
        }
    },
    methods: {
        sendFormNewUser() {
            axios.post('http://localhost:8000/auth/register', this.user)
                .then(response => console.log(response))
                .catch(error => console.log(error))
        }
    }
}
</script>

<style>
    
</style>