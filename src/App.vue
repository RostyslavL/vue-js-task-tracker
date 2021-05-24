<template>
  <div class="container">
    <Header 
      @toggle-add-task="toggleAddTask" 
      title="Task Tracker" 
      :showAddTask="showAddTask" 
    />
    <div v-show="showAddTask">
      <AddTask  @add-task="addTask"/>
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
  </div>
</template>

<script>

import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data(){
    return{
      tasks:[],
      showAddTask: false,
    }
  },
  methods:{
    toggleAddTask(){
      this.showAddTask =  !this.showAddTask
    },
    async addTask(task){

      const res = await fetch('api/tasks',{
        method: 'POST',
        headers:{
          'Content-type': 'application/json',
        },
        body: JSON.stringify(task),
      })

      const data = res.json()

      this.tasks = [...this.tasks, data]
    },
    async deleteTask(id){  
      if(confirm ('Are you sure ?')){   
        
        const res = await fetch(`api/tasks/${id}`, {
          method:'DELETE',
        })

        res.status === 200 ? this.tasks = this.tasks.filter((task) =>  task.id !== id ) : alert('Detete task Error')
      }
    },
    async toggleReminder(id){

      const taskToToggle = await this.fetchTask(id)
      const updTask = {...taskToToggle, reminder: !taskToToggle.reminder}

      const res = await fetch(`api/tasks/${id}`,{
        method: 'PUT',
        headers:{
          'Content-type': 'application/json',
        },
        body: JSON.stringify(updTask),
      })
      
      const data = res.json()

      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: data.reminder} : task)
    },
    async fetchTasks(){
      const res = await fetch('api/tasks')
      const data = await res.json()
      return data
    },
    async fetchTask(id){
      const res = await fetch(`api/tasks/${id}`)
      const data = await res.json()
      return data
    }
  },
  async created(){
    this.tasks =  await this.fetchTasks()
  }
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body{
  font-family: 'Poppins', sans-serif;
}

.container{
  max-width: 800px;
  min-height: 400px;
  margin: 30px  auto;
  border: 5px solid #000;
  padding: 30px;
  border-radius: 5px;
  overflow: auto;
  box-shadow: 5px 8px 8px 5px rgba(0,0,0, 0.8);
}

.btn{
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 20px;
  font-family: inherit;
  box-shadow: 2px 2px 4px 4px rgba(0,0,0, 0.4);
}
.btn:hover{
 transform: scale(1.025);
 transition: 1s transform ease-in-out;
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
