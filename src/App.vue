<script>
export default{
  data(){
    return{
      title:"Task List",
      Items: [{text:"First"}]
    }
  },
  methods:{
    additem: function(){
      let input = document.getElementById('itemForm')
      if(input != ''){
        this.Items.push({
          text:input.value
        })
        input.value = ""
      }
    },
    deleteItem(index){
      this.Items.splice(index,1)
    }
  }
}
</script>

<template>
  <div class="container">
    <header>
      <h1>{{ title }}</h1></header>
      <form class="form">
        <div class="input-group mb-3">
          <input type="text" class="form-control" placeholder="AddTask" id="itemForm">
          <div class="input-group-append">
            <button type="button" class="btn btn-outline-secondary" v-on:click="additem">Add</button>
          </div>
        </div>
      </form>
      <table class="table table-striped table-dark">
        <thead>
          <tr>
            <th scope="col">Tasks</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in Items">
            <th scope="row">{{ item.text }} <button type="button" v-on:click="deleteItem(index)" className="btn btn-danger">✂</button></th>
          </tr>
        </tbody>
      </table>
  </div>
</template>

<style scoped></style>
