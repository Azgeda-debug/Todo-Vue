<template>

  <main>
    <h1 class="app-title">Todo App</h1>
    <TodoAdd @AddNewTodo="AddNewTodo" />
    <TodoCreate :newTodoItem="newTodoItem" @todoDone="todoDone" @removeTodo="removeTodo" />
  </main>

</template>

<script>

import TodoAdd from './components/TodoAdd.vue';
import TodoCreate from './components/TodoCreate.vue';
export default {
    name: "App",
    data() {
      return {
        newTodoItem: [],
      }
    },
    components: 
    {
      TodoAdd,
      TodoCreate,
    },
    methods:
    {
      AddNewTodo(value)
      {
        this.newTodoItem.push({title: value, completed: false, id: Math.random()});
      },
      todoDone(id)
      {
        const index = this.newTodoItem.findIndex(el => el.id === id);
        if(index > -1)
        {
          this.newTodoItem[index].completed = true;
        }
      },
      removeTodo(id)
      {
        const index = this.newTodoItem.findIndex(el => el.id === id);
        if(index > -1)
        {
          this.newTodoItem.splice(index, 1);
        }
      }
    },
}
</script>

<style>

/* Global Settings */
*
{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body
{
  font-family: 'Times New Roman', Times, serif;
  background: rgba(0, 0, 0, 0.1);
}

/* App Styling */

main
{
  display: flex;
  align-items: center;
  flex-direction: column;
  gap: 30px;
}

.app-title
{
  color: #21c421;
}

</style>
