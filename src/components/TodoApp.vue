<template>
  <div class="container">
   <h2 class="text-center">My Vue Js Todo App</h2>
   <div class="d-flex">
     <input type="text" placeholder="Enter task" class="form-control">
     <button class="btn btn-warning rounded-0">SUBMIT</button>
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
      <td>{{task.name}}</td>
      <td>{{task.status}}</td>
      <td><div class="text-center"><span class="fa fa-pen"></span></div></td>
      <td><div class="text-center"><span class="fa fa-trash"></span></div></td>
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
  }
};
</script>
