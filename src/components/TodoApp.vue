<template>
  <div class="container">
   <h2 class="text-center">My Vue Js Todo App</h2>
   <div class="d-flex">
     <input v-model="task" type="text" placeholder="Enter task" class="form-control">
     <button @click="submitask" class="btn btn-warning rounded-0">SUBMIT</button>
   </div>
   <div class="mt-4">
      <table class="table table-bordered">
  <thead>
    <tr>
      <th scope="col">Tasks</th>
      <th scope="col">Status</th>
      <th scope="col" class="text-center">#</th>
      <th scope="col" class="text-center">#</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task,index) in tasks" :key="index">
      <td>
         <span :class="{'finished': task.status=== 'finished'}">{{task.name}}</span>
        </td>
      <td>
        <div :class="{'text-danger': task.status=== 'to-do', 'text-warning': task.status=== 'in-progrss','text-success': task.status=== 'finished'}" class="pointer" @click="changeStatus(index)"> 
          {{task.status}}
        </div>
        
        </td>
      <td>
        <div class="text-center"  @click="editTask(index)">
          <span class="fa fa-pen"></span>
        </div>
      </td>
      <td>
        <div class="text-center" @click="deleteTask(index)">
          <span class="fa fa-trash"></span>
        </div>
      </td>
    </tr>
  </tbody>
</table>
   </div>
  
  </div>
</template>

<script>
export default {
  name: "TodoApp",
  data(){
    return {
      task: "Hello task",
      editedtask: null,
      availableStatuses: ['to-do', 'in-progrss', 'finished'],
      tasks:[
        {
          name: "Read General Part",
          status: "to-do"
        },
        {
          name: "Read IT Part",
          status: "to-do"
        },
        {
          name: "Read Previus year questions",
          status: "to-do"
        }
      ]
    }
  },
  methods:{
    submitask(){
      if(this.task.length === 0) {
        alert("Please Write your task name");
      }else{
        if(this.editedtask === null){
           this.tasks.push({
          name: this.task,
          status: "to-do"
          })
        }else{
            this.tasks[this.editedtask].name = this.task;
            this.editedtask = null;
        }
       

      }
      
    },
    deleteTask(index){
      this.tasks.splice(index,1);
    },

    editTask(index){
      this.task = this.tasks[index].name;
      this.editedtask = index;
    },
    changeStatus(index){
      let newIndex = this.availableStatuses.indexOf(this.tasks[index].status);
      if(++newIndex>2) newIndex=0;
      this.tasks[index].status = this.availableStatuses[newIndex];
      //console.log(newIndex);
    }
  }
};
</script>
<style scoped>
  .pointer{
    cursor: pointer;
  }
  .finished{
    text-decoration: line-through;
  }
</style>