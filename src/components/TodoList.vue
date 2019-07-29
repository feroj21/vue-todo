<template>
  <div class="bg-box">
    <h2>To DO: </h2>
    <ul class="list-group">
        <li v-for="todo in todos">
          <todo v-bind:item="todo"></todo>
        </li>
    </ul>

    <div class="form">
      <label for="task">Task</label>
      <input type="text" v-model="taskName" placeholder="What do you need to do">
      <button @click.prevent="addTask()">Save Item</button>
    </div>
  </div>
</template>

<script type = "text/javascript" >

import Todo from '@/components/Todo'
export default {
  components: {
    Todo
  },
  data() {
    return {
      todos: [],
      taskName: ''
    };
  },
  methods: {
    /** 
     * Add task
    */
    addTask() {
      // If the task title empty then do nothing
      if (this.taskName === '') {
        return;
      }

      this.todos.push({
        title: this.taskName,
        done: false
      });

      this.taskName = '';
    }
  }
}

</script>
<style></style>
