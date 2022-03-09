<script lang="ts">
import { defineComponent } from "vue";

let id = 0;

export default defineComponent({
  props: {
    message: String,
  },
  data() {
    return {
      newTodo: "",
      todos: [
        { id: id++, text: "Learn HTML" },
        { id: id++, text: "Learn React" },
      ],
    };
  },
  methods: {
    addNewTodo() {
      this.todos.push({
        id: id++,
        text: this.newTodo,
      });
      this.newTodo = "";
    },
    removeTodo(todo: { id: number; text: string }) {
      this.todos = this.todos.filter((item) => item != todo);
    },
  },
});
</script>

<template>
  <main>
    <div class="w-full h-screen px-40 py-4 bg-gray-300">
      <div class="flex justify-around bg-white w-64 py-4 rounded-md">
        <input
          v-model="newTodo"
          @keyup.enter="addNewTodo"
          placeholder="Aa"
          class="w-44 border-2 border-gray-400 rounded-md outline-green-800 px-2"
        />

        <button
          type="button"
          class="bg-green-700 text-white rounded-md px-2"
          @click="addNewTodo"
        >
          Add
        </button>
      </div>

      <div class="flex justify-around bg-white w-64 py-4 mt-4 rounded-md">
        <ul>
          <li
            v-if="todos.length === 0"
            class="border border-gray-400 px-2 py-1 text-gray-600 rounded-md mb-2"
          >
            Todos is empty
          </li>
          <li
            v-else
            v-for="todo in todos"
            :key="todo.id"
            class="border border-gray-400 px-2 py-1 text-gray-600 rounded-md mb-2"
          >
            {{ todo.text }}
            <button
              type="button"
              class="text-white text-xl rounded-md px-2 cursor-pointer"
              @click="removeTodo(todo)"
            >
              🚫
            </button>
          </li>
        </ul>
      </div>
    </div>
  </main>
</template>
