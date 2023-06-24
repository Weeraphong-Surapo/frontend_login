<template lang="">
    <form @submit.prevent="submit">
        <div>
            <label for="email">Email</label>
            <input type="text" name="email" id="email" v-model="form.email">
        </div>
        <div>
            <label for="password">Password</label>
            <input type="password" name="password" id="password" v-model="form.password">
        </div>
        <div>
            <button type="submit">Login</button>
        </div>
    </form>
</template>
<script>
import { mapActions } from 'vuex';
export default {
    name: 'sign-in',
    data() {
        return {
            form: {
                email: '',
                password: ''
            }
        }
    },
    methods: {
        ...mapActions({
            SignIn: 'auth/SignIn'
        }),
        submit() {
            this.SignIn(this.form).then(() => {
                this.$router.replace({
                    name: 'dashboard'
                })
            }).catch(() => {
                //
            })
        }
    },
}
</script>
<style lang="">
    
</style>