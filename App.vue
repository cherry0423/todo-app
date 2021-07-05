<template>
  <main>
    <div class="container">
      <h1>欢迎使用 Sun 待办事项</h1>
      <todo-add :tid="todos.length" @add-todo="addTodo" />
      <todo-filter :selected="filter" @change-filter="filter = $event" />
      <todo-list :todos="filteredTodos" />
    </div>
  </main>
</template>

<script>
import TodoAdd from "./components/TodoAdd";
import TodoFilter from "./components/TodoFilter";
import TodoList from "./components/TodoList";
import useTodos from "./composables/useTodos.js";
import useFilteredTodos from "./composables/useFilteredTodos";

export default {
  name: "App",
  components: {
    TodoAdd,
    TodoFilter,
    TodoList,
  },
  setup() {
    const { todos, addTodo } = useTodos();
    const { filter, filteredTodos } = useFilteredTodos(todos);

    return {
      todos,
      addTodo,
      filter,
      filteredTodos,
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: Arial, Helvetica, sans-serif;
}

main {
  width: 100vw;
  min-height: 100vh;
  padding: 10vh, 0;
  display: grid;
  align-items: center;
  justify-items: center;
  background: pink;
}

.container {
  width: 60%;
  max-width: 400px;
  height: 80%;
  box-shadow: 0px 0px 24px white;
  border-radius: 24px;
  padding: 48px, 28px;
  background-color: skyblue;
}

h1 {
  margin: 24px 0;
  font-size: 28px;
  color: black;
  text-align: center;
}
</style>
