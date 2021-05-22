<template>
    <div :class="[task.reminder ? 'reminder' : '' , 'task']">
        <h3>{{ task.text }}
            <i  @click="onDelete(task.id)" class="fas fa-trash"></i>
        </h3>
        <p>{{ task.day }}</p>
    </div>   
</template>

<script>


export default {
    name:'Task',
    props:{
        task: Object,
    },
    methods:{
        onDelete(id){
           this.$emit('delete-task', id)
        },
    },
}
</script>


<style scope>

.fa-trash {
  color: red;
  
}
.task {
  background: #f4f4f4;
  margin: 20px;
  padding: 10px 20px;
  cursor: pointer;
  box-shadow: 2px 2px 4px 4px rgba(0,0,0, 0.4);
}
.task:hover{
 transform: scale(1.025);
 transition: 1s transform ease-in-out;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
