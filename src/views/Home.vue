<template>
  <div id="app">
    <div>
    <Header />
    <AddTask v-on:add-task="addTask"/>
    <Tasks v-bind:msg="msg" v-bind:tasks="tasks" v-on:del-task="deleteTask"/>
  </div>
  </div>
</template>

<script>
// import Header from '../components/layout/Header';
import AddTask from '../components/AddTask';
import Tasks from '../components/Tasks';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    // Header,
    AddTask,
    Tasks
  },
  data(){
    return {
      msg: 'Hi guys',
      tasks: [
        
      ]
    }
  },
  methods : {
    deleteTask(id){
      axios.delete(`http://localhost:3000/api/task/${id}`)
      .then(res => this.tasks = this.tasks.filter(task => task.id !== id))
      .catch(err => console.log(err));
    },
    addTask(newTask){
      const{title, done} = newTask;
      axios.post('http://localhost:3000/api/task/',{
        title,
        done
      })
      .then(res => this.tasks=[...this.tasks, res.data])
      .catch( err => console.log(err));

      axios.get('http://localhost:3000/api/task/list')
     .then(res=> this.tasks = res.data)
     .catch(err => console.log(err));
    }
  },
  created(){
     axios.get('http://localhost:3000/api/task/list')
     .then(res=> this.tasks = res.data)
     .catch(err => console.log(err));

    //  console.log(res.data);
    // fetch("http://localhost:3000/api/task/list").then(function (response) {
    //         return response.json();
    // }).then(function (result) {
    //       console.log(result);
    //     this.tasks =  result;   
    // }); 

  //   fetch('http://localhost:3000/api/task/list', { mode: 'no-cors' })
  //   // .then(stream => stream.json())
  //   // .then(data => this.tasks = data)
  //     .then(function(response) {
  //   return response.text();
  // })
  //   .catch(error => console.error(error))

    console.log(this.tasks)
  }

}
</script>

<style>
  *{
    box-sizing: border-box;
    margin:0;
    padding: 0;
  }

  body{
    font-family: Arial, Helvetica, sans-serif;
    line-height:1.4;
  }

  .btn{
    display: inline-block;
    padding: 7px 20px;
    color : white;
    background: #7D9569;
    border: none;
    cursor: pointer;
  }

  .btn:hover{
    background: #9FAA95;
  }

  
</style>
