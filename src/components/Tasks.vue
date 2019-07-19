<template>
  <div class="tasks-container">

    <slot name="tasks-header-title">
      <h1>This is default header title</h1>
    </slot>

    <div class="add-task-button" @click="addNewTask()">
      Add a new task
    </div>

      <div class="show-hide-tasks" @click="showHideTasks()"> Show / Hide tasks </div>

      <div class="added-tasks-container">
          <slot v-if="shouldShowNotes" name="task" :tasks="tasks">
            <p v-for="task in tasks" class="task-default-style" :key="task.id">{{task.name}}</p>
          </slot>
      </div>
      

  </div>
</template>


<script>
export default {
  data() {
    return {
      test: 'this is a test text',
      shouldShowNotes: true,
      tasks: [
        {id: 1, title: 'your task',name: "get milk", backgroundColor: "#F4D03F"},
        {id: 2, title: 'your task',name: "repair car", backgroundColor: "#229954"},
        {id: 3, title: 'your task',name: "get the children from school", backgroundColor: "#9B59B6"},
        {id: 4, title: 'your task',name: "buy new coat", backgroundColor: "#FFCA00"},
        {id: 5, title: 'your task',name: "finish the assignment", backgroundColor: "#005EB2"},
      ]
    }
  },
  methods: {
    addNewTask() {
      this.tasks.push({
          id: this.incrementId(),
          title:"something",
          name:"something",
          backgroundColor: this.randomColorGenerator()
        })
    },
    
    incrementId() {
      var Id = this.tasks[this.tasks.length-1].id + 1
      return Id;
    },

    randomColorGenerator() {
      return "#" + (Math.random()*0xFFFFFF<<0).toString(16)
    },

    showHideTasks() {
      if (this.shouldShowNotes) return this.shouldShowNotes = false
        return this.shouldShowNotes = true
    }
    

  }
}
</script>

<style>
.added-tasks-container {
  border: 1px solid #ccc;
  background-color:#edeef0;
  padding: 10px;
  border-radius: 5px;
}


.task-default-style {
  margin: 10px;
  display: inline-block;
  padding: 15px;
  background-color: orange;
  color: #fff;
  border-radius: 5px;
}

.add-task-button {
  display: block;
  padding: 14px;
  margin: auto;
  margin-bottom: 15px;
  width: 120px;
  border-radius: 5px;
  border: 1px solid #ccc;
  color: #111;
  background-color: orange;
}

.add-task-button:hover {
  cursor: pointer;
  background-color: #ffffff;
  color: orange;
  transition: .4s;
}

.show-hide-tasks {
  width: 160px;
  border: none;
  border: 1px solid #ccc;
  padding: 6px;
  color: #fff;
  background-color: #111;
  margin: 10px auto;
  border-radius: 5px;
}

.show-hide-tasks:hover {
  cursor: pointer;
}

.slex-fade-enter-active, .slex-fade-leave-active {
  transition: opacity .5s;
}
.slex-fade-enter, .slex-fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

</style>
