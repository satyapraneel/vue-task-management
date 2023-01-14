<template>
    <header>
        <h1>{{ title }}</h1>
        <Button v-show="homePage" :text="showAddTask ? 'Close Task' : 'Add Task'" :color="showAddTask ? 'red' : 'green'" @btn-click="$emit('btn-click')"/>
    </header>
</template>

<script>
    import Button from './Button.vue';
    export default {
        name: "Header",
        components: {
            Button,
        },
        props: {
            title: String,
            showAddTask: Boolean
        },
        computed: {
            homePage() {
                if (this.$route.path === '/') {
                    return true
                }
                return false
            }
        }
    }
</script>

<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>