<template>
<div class="container">
  <div v-show="showAddTask">
<AddTask  @add-task ="addTask"/>
  </div>
<Header @toggle-add-task="toggleAddTask" title='Task Tracker' :ShowAddTask="showAddTask" />
<Tasks :tasks="tasks" @delete-task="handleDelete" @toggleReminder="handleToggle" />
</div>
</template>
<script>
import Header from './components/Header'
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  methods:{

    toggleAddTask(){
      this.showAddTask = !this.showAddTask;

    },
    handleDelete(id){
      if(confirm("Are you sure ?")){
        this.tasks = this.tasks.filter((task)=>task.id !== id)
      }
    },
    handleToggle(id){
      this.tasks = this.tasks.map((task)=>task.id === id?{...task,reminder:!task.reminder}:task)
 
    },
    async fetchTasks(){
      const data = await fetch("api/tasks");
      const result = await data.json();
      return result;
    },
    async fetchTask(id){
      const data = await fetch(`api/task/${id}`);
      const result = await data.json();
      return result;
    },
    async addTask(task){
      const data= await fetch("api/task",{
        method:'POST',
        headers:{
          'Content-type':'application/json'
        },
        body:JSON.stringify(task)
      });
      
    }
  }
  ,
  data(){
    return{
      tasks:[ ],
      showAddTask:false
    }
  },
 async created(){
    this.tasks =await this.fetchTasks();
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>

