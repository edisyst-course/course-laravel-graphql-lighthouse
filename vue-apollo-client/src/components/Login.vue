<template>
    <div>
        <form @submit.prevent="submitLogin">
            Email <br/>
            <input type="email" v-model="email" />
            <br/><br/>
            Password <br/>
            <input type="password" v-model="password" />
            <br/><br/>
            <button type="submit">Log in</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "Login",

    data() {
        return {
            email: "",
            password: "",
        }
    },

    methods: {
        submitLogin() {
            axios
            .post(process.env.VUE_APP_SERVER_HTTP + "/api/sanctum/token", {
                email: this.email,
                password: this.password,
                device_name: navigator.userAgent,
            })
            .then( async (response) => {
                console.log("Token: " + response.data); // per ora stampo solo il token
                this.$router.push('/');
            })
            .catch( (error) => console.log(error) );
        }
    }

}
</script>
