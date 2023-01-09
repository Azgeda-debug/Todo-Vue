<template>

<div class="todo-container">
    <input type="text" v-model="newTodo" class="todo-add" @keydown="addTodoByKey" placeholder="Type here to add todo">
    <button class="todo-add-btn" @click="addTodoByClick">Add Todo</button>
</div>

</template>

<script>

export default {
    name: 'TodoApp',
    data() {
        return {
            newTodo: '',
        }
    },
    methods:
    {
        addTodoByKey(e)
        {
            if(e.key == 'Enter' && this.newTodo !== '')
            {
                this.$emit('AddNewTodo', this.newTodo);
                this.newTodo = '';
            }
        },
        addTodoByClick()
        {
            if(this.newTodo !== '')
            {
                this.$emit('AddNewTodo', this.newTodo);
                this.newTodo = '';
            }
        }
    }
}

</script>

<style scoped>

/* Input And Button Styling */
.todo-add
{
    font-size: 20px;
    border-radius: 16px;
    border: 1px solid #21c421;
    padding: 3px 0px 5px 14px;
    outline: none;
    color: #249624;
}

.todo-add-btn
{
    padding: 6px 60px;
    font-size: 22px;
    border-radius: 20px;
    border: none;
    outline: none;
    font-weight: bold;
    cursor: pointer;
    transition: all .3s ease-in-out;
    display: block;
    margin: 20px auto;
    background: rgba(38, 175, 26, 0.605);
    color: white;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.33);
}

.todo-add-btn:hover
{
    background: rgba(38, 175, 26, 0.905);
    box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.66);
}

</style>