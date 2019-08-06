<template>
    <div>
        <form @submit.prevent="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add todo...">
            <input type="submit" value="submit" class="btn">
        </form>
    </div>
</template>

<script>
//import uuid from 'uuid';
export default {
    name: "AddTodo",
    data(){
       return{
           title:'',
       } 
    },
    methods: {
        addTodo(){
            const newTodo = {
             //   id : uuid.v4(), json place holder provides an initial id
                title : this.title,
                completed : false,
            }
            //console.log(newTodo);
            //emit used to send objects/parameters to parent
            this.$emit('add-todo',newTodo);
            this.title = '';// clear the form after completion
        }
    },
}
</script>

<style scoped>
    form{
        display: flex;
    }
    input[type='text']{
        flex: 10;
        padding: 5px;
    }
    input[type='submit']{
        flex: 2;
    }
</style>


