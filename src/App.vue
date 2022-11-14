<template>
<div class="container">
<Header title='Task Tracker' />
<Tasks :tasks="tasks" />
</div>
</template>
<script>
import Header from './components/Header'
import Tasks from './components/Tasks.vue'
export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data(){
    return{
      tasks:[]
    }
  },
  created(){
    this.tasks = [
      {
        id:1,
        text:"Testing the work 1",
        day:"2022 12 06 12:00",
        reminder:true
      },
      {
        id:2,
        text:"Testing the work 2",
        day:"2022 12 06 12:00",
        reminder:true
      },
      {
        id:3,
        text:"Testing the work 3",
        day:"2022 12 06 12:00",
        reminder:true
      },
    ]
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

