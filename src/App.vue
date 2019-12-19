<template>
  <div class="bg-gray-500" id="app">
    <section>
      <h3>My Todo List</h3>
      <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" type="text" v-model="state.todo" />
      <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" @click="addTodo">Add Todo</button>
      <ul>
        <li class="w-full bg-gray-400 h-12" v-for="(todo, i) in state.todolist" :key="i">
          {{todo}}
          <button @click="removeTodo(i)">x</button>
        </li>
      </ul>
    </section>
    
  </div>
</template>

<script>
import { reactive } from "@vue/composition-api";
export default {
  setup() {
    const { state, addTodo, removeTodo } = useOurTodo();
    return {
      state,
      addTodo,
      removeTodo
    };
  }
};

function useOurTodo() {
  let state = reactive({
    todo: "",
    todolist: []
  });

  function addTodo() {
    state.todolist.push(state.todo);
    state.todo = "";
  }
  function removeTodo(i) {
    // eslint-disable-next-line no-console
    console.log(i)
    state.todolist.splice(i,1);
  }
  return {
    state,
    addTodo,
    removeTodo
  };
}
</script>

<style lang="sass">
</style>