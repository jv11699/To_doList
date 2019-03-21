<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add To-do...">
            <input type="submit" value="Add To-do" class="btn">
        </form>
    </div>
</template>

<script>
    import uuid from 'uuid';
    export default {
        name: "AddTodo",
        data(){
            return{
               title:'' //returns the data
            }
        },
        methods: {
            addTodo(e){
                e.preventDefault();
                const newTodo = {
                    id: uuid.v4(),
                    title: this.title,
                    completed: false,
                    delete:false
                }
                //send up to parent
                this.$emit('add-todo', newTodo);
                this.title = ''; //when clicked it will disappear
            }
        }
    }
</script>

<style scoped>
    form{
        display: flex;
    }
    input[type="text"]{
        flex: 10;
        padding: 5px;
    }
    input[type="submit"]{
        flex:2;
    }
</style>