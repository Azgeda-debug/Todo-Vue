<template>

<div class="todo-item-contianer">
    <div class="todo-item" v-for="item in newTodoItem" :key="item.id">
        <h1 class="todo-title" :class="{'completed': item.completed}">{{ item.title }}</h1>
        <button class="todo-done-btn" @click="todoDone(item.id)" v-if="!item.completed">Done</button>
        <img @click="removeTodo(item.id)" src="../assets/img/deleteIcon.png" alt="delete icon" class="deleteIcon">
    </div>
</div>

</template>

<script>

export default {
    name: 'TodoCreate',
    props:
    {
        newTodoItem:
        {
            type: Array,
            required: true,
        },
    },
    methods:
    {
        todoDone(id)
        {
            this.$emit('todoDone', id);
        },
        removeTodo(id)
        {
            this.$emit('removeTodo', id);
        },
    }
}

</script>

<style>

/* New Todo Items Styling */

.todo-item-contianer
{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
    padding: 10px 20px;
    flex-wrap: wrap;
}

.todo-item
{
    min-width: 120px;
    min-height: 80px;
    border: 1px solid rgb(28, 182, 28);
    border-radius: 20px;
    padding: 10px 40px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    word-break: normal;
    position: relative;
}

.todo-title
{
    letter-spacing: 1px;
    font-size: 28px;
    text-align: center;
}

.todo-done-btn
{
    padding: 6px 30px;
    font-size: 18px;
    border-radius: 20px;
    border: none;
    outline: none;
    font-weight: bold;
    cursor: pointer;
    transition: all .3s ease-in-out;
    display: block;
    margin: 20px auto 5px auto;
    background: rgba(38, 175, 26, 0.605);
    color: white;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.33);
}

.todo-done-btn:hover
{
    background: rgba(38, 175, 26, 0.905);
    box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.66);
}

.todo-title.completed
{
    text-decoration: line-through;
    opacity: 0.6;
}

.deleteIcon
{
    width: 40px;
    cursor: pointer;
    margin: 5px 0px;
    transition: all .3s ease-in-out;
}

.deleteIcon:hover
{
   transform: scale(1.2);
}

</style>