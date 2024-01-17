<script setup>
import { ref } from "vue"

const tasks= ref([{
    name: 'Task 1',
    time: 30
}, {
    name: 'Task 2',
    time: 40
}, {
    name: 'Task 3',
    time: 60
}, {
    name: 'Task 4',
    time: 45
}, {
    name: 'Task 5',
    time: 50
}]);

const taskName = ref('');
const taskTime=ref('');
const isShowModal = ref(false);
const isIndex = ref(null);
//const isIndex=ref(false);

function addNewTask(){
  console.log("Hello");

  if(taskName.value ==''){
    alert("please enter your task name");
    //taskName.value.focus();
    
  }else if(taskTime.value ==''){
    alert("please enter your task time");
  }
  else{
    console.log(taskName.value);
    const newTask={
    name: taskName.value,
    time: taskTime.value,
    } 
    tasks.value.push(newTask);  
    taskName.value='';
    taskTime.value='';
  }


}

function editTask(id,editName,editTime){
  console.log(editName);
  isShowModal.value = true;
  isIndex=id;
  console.log(isIndex);
  /*if(taskName.value ==''){
    alert("please enter your task name");
    //taskName.value.focus();
    
  }else if(taskTime.value ==''){
    alert("please enter your task time");
  }
  else{*/
   // console.log(taskName.value);
    const editTasks=ref([{
        name: editName,
        time: editTime,
    }]) 
    //tasks.value.push(newTask);  
    //taskName.value='';
    //taskTime.value='';
  //}


}

function DeleteTask(id){
  //console.log(id);
  this.tasks.splice(id, 1);
}



// function showModal () {
//   isShowModal.value = true
// }
</script>
<template>
  <section class="container mx-auto flex items-center flex-col">
    <h1 class="text-center text-2xl py-10">Task List</h1>

    <!-- <p v-for="task in tasks" :key="task.id">{{ task.name }}</p> -->
    <div class="container mx-auto flex space-x-5 justify-center m-5" v-for="(task,index) in tasks" :key="index" >
      <p> Task Name : {{ task.name }}
          Time : {{ task.time }}
          <!-- <button @click="DeleteTask(index)" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" >
            Edit
          </button> -->
          <button @click="editTask(index,task.name,task.time)" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" >
            Edit
          </button>          
      </p>
     
    </div>

    <div class="container mx-auto flex space-x-5 justify-center m-5" >
        
        <div v-if="isShowModal" >
            <div class="container mx-auto flex space-x-5 justify-center m-5"  >
                
                <p><input type="text" v-model="taskName" class="border border-gray-500 bg-white p-5" value="" /></p>
                <p><input type="number" v-model="taskTime" class="border border-gray-500 bg-white p-5"  value=""  /></p>
                <p><button @click="addNewTask()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" >
                    Edit Task
                </button></p>

            </div>
            
        </div>
    </div>




  </section>
</template>
<style scoped></style>