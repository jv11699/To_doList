<template>
    <div>
        <!--
         *This means it loops through the todos with the title
         *ESlint error because when you loop through like this you need
         *a unique key attached to this, much like in react-->
        <div v-bind:key="todo.id" v-for="todo in todos" >
            <TodoItem v-bind:todo = "todo" v-on:del-todo="$emit('del-todo',todo.id)" />
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'
    export default {
        name: "Todos",
        components: {
            TodoItem
        },
        props: ["todos"],


    }
</script>

<style scoped>

</style>