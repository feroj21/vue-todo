<template>
  <div class="todo-item">
    <div class="item todo-title">
        {{ item.title }}
    </div>
    <div class="item action">
      <a class="btn done" href="#" @click.prevent="doneTask()">✓</a>
      <a class="btn delete" href="#" @click.prevent="deleteTask()">✘</a>
    </div>
  </div>
</template>

<script type = "text/javascript" >

export default {
  props: ['item'],
  methods: {
    /**
     * Task done method
    */
    doneTask () {
      this.item.done = true
    },

    /**
     * Delete task
    */
    deleteTask () {
      this.$emit('delete-task', this.item)
    }
  }
}

</script>
<style>
.todo-item {
  display: flex;
}
.todo-title {
  width: 84%;
}
.done {
  color: #fff;
  background-color: #28a745;
  border-color: #28a745;
}

.delete {
  color: #fff;
  background-color: #dc3545;
  border-color: #dc3545;
}

</style>
