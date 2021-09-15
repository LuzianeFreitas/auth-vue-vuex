<template>
    <div class="container">
        <h1>Login</h1>
        <form @submit.prevent="login">
            <div class="form-group">
                <label for="email">E-mail</label>
                <input type="email" class="form-control" v-model="user.email">
            </div>
            <div class="form-group">
                <label for="password">Senha</label>
                <input type="password" class="form-control" v-model="user.password">
            </div>
            <button type="submit" class="btn btn-primary btn-block">Entrar</button>
            <router-link :to="{name: 'novo-usuario'}">
                Não possui uma conta? Cadastre-se aqui
            </router-link>
        </form>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
            user: {}
        }
    },
    methods: {
        login() {
            axios.post('http://localhost:8000/auth/login', this.user)
                .then(response => {
                    console.log(response)
                    localStorage.setItem('token', response.data.access_token)
                    this.$router.push({ name: 'gerentes'})
                })
                .catch(error => console.log(error))
        }
    }
}
</script>

<style scoped>
    
</style>