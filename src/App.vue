<template>
  <div id="app">
    <div class="container">
      <h1 class="title">Todo App</h1>

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
      </form>
  <table class="table table-hover table-editable" v-if="todos.length">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">Todo</th>
      <th scope="col">Update</th>
      <th scope="col">Delete</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(todo, index) in todos" :key="`${index}-${todo.item}`">
      <th scope="row">{{index + 1}}</th>
      <td>
        <input :v-model="todos[index]" :name="todoItem + index"
        :id="todoItem + index" :placeholder="todo" v-show="todo" :readonly="readonly"/>
      </td>
      <td>
        <button class="btn btn-outline-secondary update"
                type="button" id="updateButton"
                @click="updateTodo(index)">
                <span v-if="readonly">Update</span>
                <span @click="recordsUpdated" v-else>Save</span>

                <font-awesome-icon icon="edit" />
        </button>
      </td>
      <td>
        <button class="btn btn-outline-secondary delete"
        type="button" id="deleteButton" @click="deleteTodo(index)">Delete
        <font-awesome-icon icon="trash" />
        </button>
      </td>
    </tr>
  </tbody>
</table>
<div v-if="updated">
  <p style="color: #34eb77; font-size: 25px;">The records updated successfully!!!</p>
</div>
      </div>
   </div>
</template>
<script>
export default {
  name: 'App',
  data() {
    return {
      todos: [],
      updated: false,
      todoUpdate: '',
      readonly: true,
      todoItem: 'todoItem',
      todo: [{
        item: '',
      }],
      updateTodoItem: [{
        item: '',
      }],
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
      this.readonly = !this.readonly;
    },
    recordsUpdated() {
      this.updated = true;
      setTimeout(() => {
        this.updated = false;
      }, 4000);
    },
  },
};
</script>
<style>
body{
  background-image: linear-gradient(to right, #f5f7fa , #c3cfe2);
}
#app {
  width: 40%;
  margin: auto;
  padding-top: 250px;
}
.table {
  text-align: white;
}
.title {
  text-align: center;
  margin-bottom: 100px;
}
</style>
