<script>
export default{
    props:{
        userlist:{
            type:Object,
            required: true
        },
        userindex:{
            type:Number,
            required:true
        },
        deleteFunc:{
            type:Function,
            required:true
        }
    }
}
</script>
<template>
<div>
    <h2>{{ userlist.tasks }}</h2>
    <button type="button" v-on:click="deleteFunc(userindex)">Удалить</button>
</div>
</template>
<style scoped>
button{
  width: 250px;
  border: 0;
  font-size: 30px;
  height: 40px;
  background-color: #e134eb;
  color: #ffffff;
  cursor: pointer;
}
</style>