<template>
    <div class = "todo-item" v-bind:class ="{'is-complete':todo.completed, 'todo-itemOnDel':todo.delete}">
        <p>
            <input contenteditable="false" type = "checkbox" v-on:change = "markComplete" >
            <b contenteditable="true">{{todo.title}}</b>
            <button contenteditable="false"  @click="$emit('del-todo', todo.id)" class = "del" v-on:click = "deleteItem()" > x </button>
        </p>
    </div>
</template>

<script>
    export default {

        name: "TodoItem",
        props: ["todo"],
        methods: {
            markComplete(){
                this.todo.completed =  !this.todo.completed; //makes the todo boolean false
            },
            deleteItem(){
                this.todo.delete =  true;
            },
            emit(){
               //this.emit()"$emit('del-todo', todo.id)"
            }
        }

    }
</script>

<style scoped>
     .todo-itemOnDel {

        position: relative;
        animation-name: DELETE;
        animation-duration: 1s;


    }
    .todo-item {
        background: lightgrey;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }
    .is-complete{
        text-decoration: line-through;
    }
    .del{
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;

    }
    b{
        font-weight: normal;
    }
    @keyframes DELETE {
     from {background-color:lightgrey; left:200px}
        to{background-color:red; left:1800px }
    }

</style>