<template>
  <div id="app">
    <div>
      <tabs>
        <tab name="Work">
          <todo-list v-bind:todos="todos1"></todo-list>
          <create-todo v-on:create-todo="createTodo1"></create-todo>
        </tab>
        <tab name="Food">
          <todo-list v-bind:todos="todos2"></todo-list>
          <create-todo v-on:create-todo="createTodo2"></create-todo>
        </tab>
        <tab name="Social">
          <todo-list v-bind:todos="todos3"></todo-list>
          <create-todo v-on:create-todo="createTodo3"></create-todo>
        </tab>
        <tab name="Kids">
          <todo-list v-bind:todos="todos4"></todo-list>
          <create-todo v-on:create-todo="createTodo4"></create-todo>
        </tab>
      </tabs>

  </div>
</div>
</template>

<script>
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo
  },
  data() {
    return {
      todos1: [{title: 'Test naslov',
        project: 'test vsebina',
        done: false}],
      todos2: [],
      todos3: [],
      todos4: [],
    };
  },
  methods: {
    createTodo1(newTodo) {
      this.todos1.push(newTodo);
    },
    createTodo2(newTodo) {
      this.todos2.push(newTodo);
    },
    createTodo3(newTodo) {
      this.todos3.push(newTodo);
    },
    createTodo4(newTodo) {
      this.todos4.push(newTodo);
    },
  }
}
</script>

<style>
a {
  background-color: #f3e7ea;
}

body  {
  background-color: #eaf1fa;
}

#app {
  position: relative;
  width: 800px;
  left: 27%;
}

.tabs-component {
  margin: 4em 0;
}

.tabs-component-tabs {
  border: solid 1px #ddd;
  border-radius: 6px;
  margin-bottom: 5px;
}

@media (min-width: 700px) {
  .tabs-component-tabs {
    border: 0;
    align-items: stretch;
    display: flex;
    justify-content: flex-start;
    margin-bottom: -1px;
  }
}

.tabs-component-tab {
  width: 120px;
  color: #999;
  font-size: 14px;
  font-weight: 600;
  margin-right: 0;
  list-style: none;
}

.tabs-component-tab {
  border: 1px #ddd;
}

.tabs-component-tab:hover {
  color: #666;
}

.tabs-component-tab.is-active {
  color: #000;
}

.tabs-component-tab.is-disabled * {
  color: #cdcdcd;
  cursor: not-allowed !important;
}

@media (min-width: 700px) {
  .tabs-component-tab {
    background-color: #fff;
    border: solid 1px #ddd;
    border-radius: 3px 3px 0 0;
    transform: translateY(2px);
    transition: transform .3s ease;
  }

  .tabs-component-tab.is-active {
    border: solid 1px #fff;
    z-index: 2;
    transform: translateY(0);
  }
}

.tabs-component-tab-a {
  text-align: center;
  align-items: center;
  color: inherit;
  display: flex;
  padding: .75em 1em;
  text-decoration: none;
}

.tabs-component-panels {
  padding: 4em 0;
}

@media (min-width: 700px) {
  .tabs-component-panels {
    border-top-left-radius: 0;
    background-color: #fff;
    border: solid 1px #ddd;
    border-radius: 0 6px 6px 6px;
    box-shadow: 0 0 10px rgba(0, 0, 0, .05);
    padding: 4em 2em;
    background-color: #f3e7ea;
  }
}
</style>
