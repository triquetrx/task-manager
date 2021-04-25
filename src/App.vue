<template>
<head></head>
<body>
  <div class="b-container">
      <Header 
        title="Task Manager"
      />
    <!--<div class="navbarline"></div>-->
  </div>
  <div v-if="showAddTask">
    <AddTask @closeAll="closeAdd" @add-Task="addtask"/>
  </div>
  <div v-show="showTasks">
    <Tasks @toggle-reminder="toggleReminder" @view-more="viewMore" :tasks="tasks"/>
  </div>
  <div class="d-flex justify-content-center">
    <Button @add-new-task="addNewTask" class="p-4 w-50 bd-highlight" id="box1" text="Add New Task" />
    <Button @clear-task ="cleartasks" class="p-3 bd-highlight" id="box2" text=" Completed All" />
  </div>
</body>
<footer class="footer-copyright text-center py-3" id="footer">
  <h5>© 2021 Copyright: Designed by triquetrx</h5>
</footer>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import Button from './components/Button'
import AddTask from './components/AddTask'
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    Button,
    AddTask
  },
  data(){
    return{
      tasks: [],
      showAddTask:false,
      showTasks:true
    }
  },
  methods:{
    showTasks(showAddTask){
      this.showTasks = !this.showAddTask
    },
    closeAdd(){
      this.showAddTask=!this.showAddTask
    },
    addNewTask(){
      this.showAddTask=!this.showAddTask
    },
    cleartasks(){
      this.tasks = !this.tasks
    },
    addtask(task){
      this.tasks = [...this.tasks, task]
    },
    viewMore(id){
      if(confirm("Are You Sure ?")){
        this.tasks = this.tasks.filter((task)=>task.id !==id)
      }
    },
    toggleReminder(id){
      this.tasks =this.tasks.map((task)=> task.id===id ? {...task,reminder: !task.reminder}:task)
    },
  },
  created(){
    this.tasks = [
      {
        id: 1,
        text: 'Completing Homework',
        day:'30th April at 2:00pm',
        priority: {label: 'low', prio: 2},
        reminder: true,
      },
      {
        id:2,
        text: 'Meeting at School',
        day: '30th April at 4:00pm',
        priority: {label: 'low', prio: 2},
        reminder: true,

      },
      {
        id:3,
        text: 'Movies with friends',
        day: '30th April at 6:00pm',
        priority: {label: 'low', prio: 2},
        reminder: false,
      }
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
  background:#181818;
}
body{
  color: #fff;
  background:#080705;
  padding:2px;
}
footer{
  position: fixed;
  padding: 10px 10px 0px 10px;
  bottom: 0;
  width: 100%;
  background: rgba(10, 10, 10, 0.4);
}
.press{
  margin-top:40px;
  font-weight: bolder;
}
.custom-icon {
   font-size: 2rem;
}
#box1{
  font-weight: bold;
  display: inline-block;
  background: #9E2B25;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
  transition: 0.5s;
}
#box2{
  font-weight: bold;
  display: inline-block;
  word-wrap: break-word;
  background: #009B72;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
  transition: 0.5s;
}
#box2:hover{
  box-shadow: 1px 1px 10px whitesmoke;
  transition-duration: ease-in;
}
#box1:hover{
  box-shadow: 1px 1px 10px whitesmoke;
  transition-duration: ease-in;
}
#box3{
  font-weight: bold;
  display: inline-block;
  background: whitesmoke;
  word-wrap: break-word;
  color: #000;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
  transition: 0.5s;
}
#box3:hover{
  box-shadow: 1px 1px 10px whitesmoke;
  transition-duration: ease-in;
}
.navbarline{
  justify-content: center;
  width:10000px;
  height: 0.01rem;
  margin-left: -20px;
  margin-top: -28px;
  background-color: rgb(245, 245, 245);
  opacity: 50%;
  box-shadow: 0px 1px 10px whitesmoke;
}
.count{
  margin-right:10px;
  background-color: #9E2B25;
  width:12rem;
  height: 30px;
  border-radius: 10px;
  font-weight: bold;
}
</style>
