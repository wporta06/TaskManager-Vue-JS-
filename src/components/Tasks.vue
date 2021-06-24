<template>
    <div class="card mb-1 text-left">
      <ul class="list-group  ">
        <li class="list-group-item shadow p-3 mb-5 bg-light rounded " v-for="(task,index) in tasks" :key="index">
          <div :class="task.completed ? 'completed' : ''">{{task.body}}</div>

          <!-- for delete task & complet tasks   -->
          <div class="icons">
            <i class="fas fa-check-circle " @click.prevent="completeTask(task)"></i>
            <i class="fas fa-trash-alt ml-3" @click.prevent="deleteTask(index)"></i>
          </div>
        </li>
      </ul>
    </div>
</template>

<script>
export default {
  props: {
    tasks: null
  },
  methods: {
    completeTask(task){
      this.$emit("completeTaskEvent", task); //send event and where is it
    },
    deleteTask(index){
      this.$emit("deleteTaskEvent", index)
    }
  }

};
</script>

<style scoped>
.completed{
  color: rgb(255, 0, 0);
  justify-content: space-between;
  
}
.list-group-item{
  display:flex;
  justify-content: space-between;
}
</style>



