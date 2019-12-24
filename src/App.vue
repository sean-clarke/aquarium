<template>
    <div id="app">
        <router-view />
    </div>
</template>

<script>
    export default {
        mounted() {
            this.$router.push({name: 'login'});
        },
    }
</script>

<style>
    #app {
        width: 100vw;
        height: 100vh;
        box-sizing: border-box;
    }
</style>
