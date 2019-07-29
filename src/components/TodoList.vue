<template>
<div class="task-list-wrapper">
  <div class="bg-box">
      <h2>To Do: </h2>
      <ul class="list-group">
          <li v-for="(todo, index) in incompleteTask" :key="index">
            <todo v-bind:item="todo" @delete-task="deleteTask"></todo>
          </li>
      </ul>

      <div class="form mt-20">
        <div class="form-group">
          <label class="label" for="task">Task</label>
          <input class="input-field" type="text" v-model="taskName" placeholder="What do you need to do">
        </div>
        <div class="action-group mt-20 text-right">
            <button class="btn btn-primary" @click.prevent="addTask()">Save Item</button>
        </div>
      </div>
    </div>

    <div class="bg-box mt-20" v-if="completedTask.length">
      <h2>Completed Tasks </h2>
      <ul class="list-group">
          <li v-for="(todo, index) in completedTask" :key="index">
            {{ todo.title }}
          </li>
      </ul>
    </div>
</div>
</template>

<script type = "text/javascript" >

import Todo from '@/components/Todo'
export default {
  components: {
    Todo
  },
  data () {
    return {
      todos: [],
      taskName: ''
    }
  },
  computed: {
    /**
     * Return incomplete task
    */
    incompleteTask () {
      return this.todos.filter(todo => {
        return todo.done === false
      })
    },

    /**
     * Return completed task
    */
    completedTask () {
      return this.todos.filter(todo => {
        return todo.done === true
      })
    }
  },
  methods: {
    /**
     * Add task
    */
    addTask () {
      // If the task title empty then do nothing
      if (this.taskName === '') {
        return
      }

      this.todos.push({
        title: this.taskName,
        done: false
      })

      this.taskName = ''
    },

    /**
    *@param {Object} item
    */
    deleteTask (item) {
      let index = this.todos.indexOf(item)

      if (index > -1) {
        this.todos.splice(index, 1)
      }
    }
  }
}

</script>
<style></style>
