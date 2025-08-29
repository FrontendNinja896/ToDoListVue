<script>
import Tasks from './components/Tasks.vue'
export default{
  components:{Tasks},
  data(){
    return{
      title:"Список дел",
      task:"",
      UserTask:[],
      error:""
    }
  },
  methods:{
    AddTask(){
      if(this.task == ""){
        this.error = "Ошибка!Вы не ввели задачу"
        return
      }
      else if(this.task.length < 3){
        this.error = "Ошибка! Длинна задачи меньше 3-х символов"
        return
      }
      this.error = ""
      this.UserTask.push({
        tasks: this.task
      })
    },
    DeleteTask(index){
      this.UserTask.splice(index,1)
    }
  }
}
</script>

<template>
  <h1>{{ title }}</h1>
  <form method="post" className="AddTaskForm">
    <p>Задача:</p>
    <input type="text" v-model="task"/>
    <button type="button" v-on:click="AddTask()">Добавить задачу</button>
    <p>{{ error }}</p>
    <Tasks v-for="el,index in UserTask" :key="index" :userlist="el" :delete-func="DeleteTask" :userindex="index"/>
  </form>
</template>

<style scoped>
h1{
  text-align: center;
  margin-top: 50px;
}
.AddTaskForm{
  display: flex;
  flex-direction: column;
  gap:10px
}
input,button{
  width: 250px;
  height: 20px;
}
button{
  border: 0;
  font-size: 30px;
  height: 40px;
  background-color: #e134eb;
  color: #ffffff;
  cursor: pointer;
}
button:hover{
  background-color: #27cf51;
}
p{
  font-size: 30px;
}
</style>
