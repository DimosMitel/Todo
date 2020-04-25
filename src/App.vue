<template>
  <div id="app">
    <div class="container">
      <form class=" col-lg-6 offset-lg-3">
        <div class="row justify-content-center" >
          <div class="input-group mb-3">
            <input type="text" class="form-control" v-model="todo.item"
            placeholder="Todo">
             <div class="input-group-append">
               <button class="btn btn-outline-secondary"
                type="button" id="button-addon2" @click="addTodo">Add
                </button>
            </div>
          </div>
        </div>

        <ul v-for="(todo, index) in todos" :key="todo">
            <li>
            <span v-if="isUpdate">{{todo}}</span>
            <span v-else>
              <input type="text" class="form-control" v-model="todo.item"
              placeholder="Todo">
            </span>
            <button class="btn btn-outline-secondary delete"
                type="button" id="button-addon3" @click="deleteTodo(index)">Delete
            </button>
            <button class="btn btn-outline-secondary update"
                type="button" id="button-addon3" @click="updateTodo()">Update
            </button>
            </li>
        </ul>
      </form>

        </div>
   </div>
</template>
<script>
export default {
  name: 'App',
  data() {
    return {
      todos: [],
      todo: [{
        item: '',
      }],
      isUpdate: true,
    };
  },
  methods: {
    addTodo() {
      this.todos.push(this.todo.item);
    },
    deleteTodo(i) {
      this.todos.splice(i, 1);
    },
    updateTodo() {
      this.isUpdate = false;
    },
  },
};
</script>
