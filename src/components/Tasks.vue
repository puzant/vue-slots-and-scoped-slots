<template>
  <div class="tasks-container">
    <slot name="tasks-header-title">
      <h1>This is default header title</h1>
    </slot>
    <slot name="task" :tasks="tasks">
      <p v-for="task in tasks" class="task-default-style" :key="task.id">{{task.name}}</p>
    </slot>
  </div>
</template>


<script>
export default {
  data() {
    return {
      test: 'this is a test text',
      tasks: [
        {id: 1, name: "get milk", backgroundColor: "#F4D03F"},
        {id: 2, name: "repair car", backgroundColor: "#229954"},
        {id: 3, name: "get the children from school", backgroundColor: "#9B59B6"},
        {id: 4, name: "buy new coat", backgroundColor: "#FFCA00"},
        {id: 5, name: "finish the assignment", backgroundColor: "#005EB2"},
      ]
    }
  }
}
</script>

<style>

.task-default-style {
  margin: 10px;
  display: inline-block;
  padding: 15px;
  background-color: orange;
  color: #fff;
  border-radius: 5px;
}

</style>
