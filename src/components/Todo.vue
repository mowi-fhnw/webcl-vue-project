<template>
  <h1>Todo List</h1>

  <div class="holder">
    <button id="plus" autofocus> + </button>
    <button id="fortune"> fortune! </button>

    <div class="table" id="todoContainer"></div>

    <div>Tasks: <span id="numberOfTasks">0</span></div>
    <div>Open:  <span id="openTasks"    >0</span></div>
  </div>
</template>

<script>
import {TodoController, TodoOpenView, TodoTotalView, TodoItemsView} from '@/assets/todo/todo.js';

export default {
  name: 'Todo',
  mounted() {
    const todoController = TodoController();

    // binding of the main view
    document.getElementById('plus').onclick    = () => todoController.addTodo();
    document.getElementById('fortune').onclick = () => todoController.addFortuneTodo();

    // create the sub-views, incl. binding
    TodoItemsView(todoController, document.getElementById('todoContainer'));
    TodoTotalView(todoController, document.getElementById('numberOfTasks'));
    TodoOpenView (todoController, document.getElementById('openTasks'));

    // init the model
    todoController.addTodo();
  }
}

</script>

<style scoped>
body {
  margin-top:     2em;
  font-family:    "Helvetica Neue", sans-serif;
}
main {
  max-width:  40em;
  margin:     auto;
  padding:    2em;
  box-shadow: 0 4px  8px 0 rgba(0, 0, 0, 0.2),
  0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
h1 {
  font-family: "Comic Sans MS", cursive, sans-serif;
  text-align: center;
}
.holder {
  margin: 0 3em 0 3em;
}
input[type=text] {
  font-family:    "Comic Sans MS", cursive, sans-serif;
  font-size:      1.1em;
  color:          darkblue;
  border-width:   0 0 1px 0;
}
input[type=text]:focus {
  border-color:   orange;
  outline:        transparent none 0;
}
#todoContainer {
  display:        grid;
  grid-column-gap: 0.5em;
  grid-template-columns: 1.7em auto auto;
  margin-bottom:  0.5em ;
}
#plus, #fortune {
  position: relative;
  top: -1em;
}
.delete {
  background-color: transparent;
  border: none;
  color: red;
  font-size: 1.3em;
}
input.invalid {
  color: red;
}

</style>
