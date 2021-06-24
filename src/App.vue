<template>
  <div id="app">
    <h3>{{title}}</h3>
    <Tasks v-bind:tasks="tasks" v-on:completeTaskEvent="completeTask" v-on:deleteTaskEvent="deleteTask"></Tasks>
    <input  class="form-control mb-2" @keyup.enter="addNewTask" type="text" v-model="newTask" >
    <button  class="btn btn-success btn-block" v-on:click="addNewTask">Add new Task</button>
  </div>
</template>


<script>

import Tasks from "@/components/Tasks";

export default {
  name: 'app',
  components: {
    Tasks
  },
  data(){
    return{
      title:"All Task ",
      newTask: null,
      tasks:[{
        body:"Go to shop1",
        completed: false
      },
      {
        body:"Go to shop2",
        completed: false
      },
      {
        body:"Go to shop3",
        completed: false
      },
      {
        body:"Go to shop4",
        completed: false
      },
      ]
    }
  },
  methods: {
    addNewTask(){
        console.log("addddd");
      this.tasks.push({     //add task to tasks
        body: this.newTask,
        completed: false
      });
      this.newTask= null;   //to empty input after add task
    },
    completeTask(task){
       console.log("done"+task);
      task.completed= !task.completed;
    },
    deleteTask(index){
        console.log("delete task " +index);
      this.tasks.splice(index, 1);
    }

  }
}

</script>

<style>

#app{
  margin-top:60px;

}
.card{
  padding: 20px;
  background: #eee;
}

</style>
