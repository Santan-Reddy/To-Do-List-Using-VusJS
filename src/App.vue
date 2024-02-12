<script setup>
import {ref} from 'vue';

const task=ref('')
const todos=ref([])

const submit_task=()=>{
  if(task.value.length!==0){
    todos.value.push({
      name:task.value,
      status:'To-Do'
    })
  }
  console.log(todos);
  task.value=''
}
</script>

<template>
  <div class="container">
  <h1>To-Do List Application</h1>
    <div class="container_input">
      <input type="text" placeholder="Enter the task To-Do" v-model="task" @keyup.enter="submit_task">
      <button @click="submit_task">Submit</button>
    </div>
    <div class="container_todo">
      <div class="container_todo_list">
        <div class="heading">
          <span>Task</span>
          <span>Status</span>
        </div>
        <div class="tasks" 
        v-for="(order, index) in todos"
        :key="index"
        >
          <span>{{order.name}}</span>
          <span>{{order.status}}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
*{
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  
}
.container{
  background-color: rgba(14, 87, 14, 0.422);
  max-width: 50vw;
  margin: auto;
  padding: 2rem;
  border-radius: 1rem;
  font-size: 1rem;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  &_input{
    display: flex;
    gap: 1rem;
    input{
      padding: 1rem 1.5rem;
      border: none;
      background-color: greenyellow;
      color: black;
      border-radius: 1rem;
    }
    button{
      padding-left: 1rem;
      padding-right: 1rem;
      background-color: rgba(44, 169, 44, 0.815);
      border-radius: 1rem;
      color: white;
      cursor: pointer;
      border: none;
    }

  }
  &_todo{
    width: 80%;
    margin-top: 2rem;
    background-color: red;
    padding: 1rem;
    border-radius: 1rem;
    background-color: rgba(14, 135, 63, 0.539);
    &_list{
      display: flex;
      flex-direction: column;
      font-size: 1.2rem;
      // align-items: ;
      .heading{
        display: grid;
        grid-template-columns: 1fr 0.5fr;
        // gap: 2rem;
        span{
          font-weight: 900;
          text-align: center;
          padding: .5rem;

        }
      }
      .tasks{
        display: grid;
        grid-template-columns: 1fr 0.5fr;
        // gap: 2rem;
        span{
          padding: .5rem;
          text-align: center;
        }
      }
    }
  }
}

</style>
