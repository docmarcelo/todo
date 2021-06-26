<template>
  <div class="" id="app">

    <div class="container grid-xs py-2">
    <img class="img-responsive img-logo" src="@/assets/logo.png" alt="logo marca da suite-case">
    <form @submit.prevent="addTdo(todo)">
      <div class="input-group">
        <input type="text" v-model="todo.description" class="form-input" placeholder="Novo todo" name="" id="">
        <button class="btn btn-primary input-group-btn">Adicionar</button>
      </div>
    </form>
        <div class="todo-list">
        <todo v-for="t in todos" :key="t.id" @toggle="toggleTodo" :todo="t" />

        </div>
      </div>
    </div>
  
</template>

<script>
import Todo from './components/Todo';

export default{
  name: "app",
  components: { Todo },
  data() {
    return { todos: [], todo:{cheked: false} };
    },
  methods:{
      addTdo(todo){
        todo.id = Date.now();
        this.todos.push(todo);
        this.todo = {cheked:false};
      },
      toggleTodo(todo){
        const index = this.todos.findIndex(item => item.id === todo.id);
        if(index > -1){
          const checked = !this.todos[index].checked;
          this.$set(this.todos, index, {...this.todos[index], checked});
        }

      }
  }
};
</script>

<style scoped>
.img-logo{
  max-width: 200px;
  margin: 0 auto;
  padding-bottom: 20px;

}
  
</style>
  