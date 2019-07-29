<template>
  <div class="todo-item">
    <div class="item todo-title">
        {{ item.title }}
    </div>
    <div class="item action">
      <a href="#">Done</a>
      <a href="#">Delete</a>
    </div>
  </div>
</template>

<script type = "text/javascript" >

export default {
  props: ['item'],
  mounted() {
    console.log(this.item);
  }
}

</script>
<style>
.todo-item {
  display: flex;
}
</style>
