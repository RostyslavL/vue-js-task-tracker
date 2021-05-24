<template>
  <div class="container">
    <Header 
      @toggle-add-task="toggleAddTask" 
      title="Task Tracker" 
      :showAddTask="showAddTask" 
    />
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</template>

<script>

import Header from './components/Header'
import Footer from './components/Footer'


export default {
  name: 'App',
  components: {
    Header,
    Footer
  },
  data(){
    return{
      showAddTask: false,
    }
  },
 methods:{
   toggleAddTask(){
      this.showAddTask =  !this.showAddTask
    },
 },
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
