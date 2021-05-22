<template>
  <div class="container">
    <Header title="Task Tracker"/>
    <Tasks :tasks="tasks"/>
  </div>
</template>

<script>

import Header from './components/Header'
import Tasks from './components/Tasks'

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
        id: 1,
        text: 'Doctors Appointment',
        day: 'March 5th at 2:30pm',
        reminder: true
      },
      {
        id: 2,
        text: 'Meeting with boss',
        day: 'March 6th at 1:30pm',
        reminder: true
      },
      {
        id: 3,
        text: 'Food shopping',
        day: 'March 7th at 2:00pm',
        reminder: false
      }
    ]
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
}

</style>
