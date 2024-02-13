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

  // if(editing.value){
  //   console.log(todos);
  //   todos.value[index].name=task.value
  //   editing.value=null
  // }

  task.value=''

}

function deleteTask(index) {
  const temp=todos.value.splice(index,1)
  console.log(temp);
} 
const editing=ref(null)
function editTask(index) {
  editing.value=!null
  task.value=todos.value[index].name
}

</script>

<template>
  <div class="main-container">

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
          <span @click="editTask(index)" class="editOption">
            Edit
          </span>
          <span @click="deleteTask(index)" class="deleteOption">
            Delete
          </span>
        </div>
      </div>
    </div>
  </div>
</div>

</template>

<style scoped lang="scss">
*{
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
body{
  margin: 0;
}
// .main-container{
//   background-color: rgba(14, 87, 14, 0.422);
//   height: 90vh;
// }
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
      outline: none;
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
        grid-template-columns: 1fr 0.5fr 0.2fr 0.2fr;
        gap: .2rem;
        span{
          font-weight: 900;
          text-align: center;
          padding: .5rem;

        }
      }
      .tasks{
        display: grid;
        grid-template-columns: 1fr 0.5fr 0.2fr 0.2fr;
        gap: .2rem;
        span{
          padding: .5rem;
          text-align: center;
          margin-top: 5px;
        }
        .deleteOption{
          color: rgba(255, 0, 0, 0.745);
          background-color: rgba(100, 56, 56, 0.517);
          border-radius: 1rem;
          cursor: pointer;
          // display: flex;
          // justify-content: center;
          // align-items: center;
        }
        .editOption{
          color: rgba(0, 255, 98, 0.745);
          background-color: rgba(56, 60, 100, 0.517);
          border-radius: 1rem;
          cursor: pointer;
          // display: flex;
          // justify-content: center;
          // align-items: center;
        }
      }
    }
  }
}

</style>
