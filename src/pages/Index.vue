<template>
  <q-page class="flex flex-center">
    <img
      alt="focus"
      src="~assets/focus.jpg"
      class="main-image"
    >
    <div class="overlay">
      <p class="main-text">What is your focus for today?</p>
      <div class="row q-pa-sm" style=" background-color: rgba(255,255,255,0.7); margin-top: 10px; color: white">
        <q-input @keyup.enter="addTask" class="col" color="black" v-model="newTask" placeholder="Add a task"   dense>


          <template v-slot:append>
            <q-btn @click="addTask" round dense flat icon="add" />
          </template>
        </q-input>
      </div>
      <q-list class="todo-list"
      separator>
        <q-item
          v-for="(task, index) in tasks"
          :key="task.title"
          :class="{'done': task.done}"
          @click="task.done = !task.done"
          clickable
          v-ripple>
          <div style="display: flex; justify-content: space-between">
          <q-item-section avatar>
            <q-checkbox class="no-pointer-events" v-model="task.done" val="teal" color=primary />
          </q-item-section>
          <q-item-section>
            <q-item-label> {{ task.title }} </q-item-label>
          </q-item-section>
          </div>
          <div>
          <q-item-section class="trash" v-if="task.done" >
            <button @click.stop="deleteTask(index)">
            <q-icon name="delete"></q-icon>
            </button>
          </q-item-section>
          </div>
        </q-item>
      </q-list>
    </div>

  </q-page>
</template>

<script>
export default {
  data(){
    return{
      newTask:'',
      tasks:[
        {
          title: 'Kiss my girl',
          done: true
        },
        {
          title: 'Finish todo app',
          done: false
        },
        {
          title: 'Start trustme app',
          done: true
        }
      ]
    }
  },
  methods:{
    addTask(){
      this.tasks.push({
        title: this.newTask,
        done: false
      })
    },
    deleteTask(index){

        this.$q.dialog({
          title: 'Confirm',
          message: 'Would you like to delete?',
          cancel: true,
          color: 'red',
          persistent: true
        }).onOk(() => {
          this.tasks.splice(index, 1);
          this.$q.notify({
            message: 'Task deleted',
            color: 'primary'})
        })
    }
  }

}
</script>


