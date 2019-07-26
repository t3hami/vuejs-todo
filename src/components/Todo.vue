<template>  
  <div class="todo container">
    <h1>Welcome to Vue.js To Do App</h1>
    <div class="form-group">
        <input type="text" v-model="text" class="form-group"  @keyup="checkEnter">
        <button @click="add" type="button" class="btn btn-primary add">Add</button>
    </div>
    <ol>
        <li v-for="(todo, index) in todos" :key="index">
            <span v-bind:class="{ done: todo.isDone }">{{todo.description}}</span>
            <pre>  </pre>
            <div id="del-chk">
                <input type="checkbox" class="form-check-input" v-model="todo.isDone" value="">
                <a @click="deleteTodo(index)" class="delete" href="#">Delete</a> 
            </div>          
        </li>
    </ol>
    
  </div>
</template>

<script>
import { constants } from 'crypto';
export default {
  name: 'Todo',
  methods: {
      add() {
          this.todos.push({ description: this.text, isDone: false});
          this.text = "";
      },
      deleteTodo(index) {
          this.todos.splice(index, 1);
      },
      checkEnter(e) {
          if (e.keyCode === 13) this.add();
      }
  },
  data() {
      return {
          text: "",
          todos: [
              { description: "A", isDone: true },
              { description: "B", isDone: false },
              { description: "C", isDone: false },
              { description: "D", isDone: true },
              { description: "E", isDone: false }
          ]
        }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
  text-align: left;
  text-indent: 10px;
}
a {
  color: #42b983;
}
pre {
    display: inline;
}
.add {
    background-color: #42b983;
}
#del-chk {
    float: right;
}
input[type='checkbox'] {
    float: right;
}
.done {
    text-decoration: line-through;
}
</style>
