<template>
    <div id="login-page">
        <div id="login-container">
            <Clock />
            <div id="login-form">
                <form v-if="!immutable" @submit.prevent="submit">
                    <p id="password-title">password:</p>
                    <input id="password" type="password" v-model="password" :placeholder="passwordLabel" :readonly="logging" :class="{'error': error}" />
                </form>
                <div v-else id="password" class="immutable"></div>
            </div>
        </div>
    </div>
</template>

<script>
    import Clock from '@/components/Clock.vue'

    export default {
        name: 'login',
        components: { Clock },
        props: [],
        mounted() {
        },
        methods: {
            submit() {
                this.logging = true;
            }
        }
    }
</script>

<style>
    #login-page {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
        color: white;
        background-image: url('../assets/images/background.jpg');
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
        font-family: 'SourceCodePro', monospace;
    }

    #login-container {
        margin: 0 auto 0 8%;
        padding: 64px;
        background-color: rgba(0, 0, 0, 0.8);
        border-radius: 8px;
    }

    #password-title {
        margin: 0 0 8px;
    }

    #password {
        padding: 8px 16px;
        border: none;
        border-radius: 4px;
        color: #fff;
        background-color: rgba(255, 255, 255, 0.1);
        text-align: center;
    }

    #password:hover {
        background-color: rgba(255, 255, 255, 0.125);
    }

    #password:focus {
        background-color: rgba(255, 255, 255, 0.15);
    }
</style>
