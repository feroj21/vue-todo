<template>
  <div class="todo-item">
    <div class="item todo-title">
        {{ item.title }}
    </div>
    <div class="item action">
      <a href="#" @click.prevent="doneTask()">Done</a>
      <a href="#" @click.prevent="deleteTask()">Delete</a>
    </div>
  </div>
</template>

<script type = "text/javascript" >

export default {
  props: ['item'],
  mounted() {
    console.log(this.item);
  },
  methods: {
    doneTask() {
      this.item.done = true;
    },

    deleteTask() {
      this.$emit('delete-task', this.item);
    }
  }
}

</script>
<style>
.todo-item {
  display: flex;
}
</style>
