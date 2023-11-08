<template>
  <q-page class="flex flex-center">
    <img
      alt="Quasar logo"
      src="~assets/focus.jpg"
      class="main-image"
    >
    <div class="overlay">
      <p class="main-text">What is your focus for today?</p>
      <q-list class="todo-list"
      separator
      bordered>
        <q-item
          v-for="task in tasks"
          :key="task.title"
          clickable
          @click="task.done = !task.done"
          v-ripple>
          <q-item-section avatar>
            <q-checkbox class="no-pointer-events" v-model="task.done" val="teal" color=primary />
          </q-item-section>
          <q-item-section>
            <q-item-label> {{ task.title }} </q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </div>

  </q-page>
</template>

<script>
export default {
  data(){
    return{
      tasks:[
        {
          title: 'Kiss my girl',
          done: false
        },
        {
          title: 'Finish todo app',
          done: false
        },
        {
          title: 'Start trustme app',
          done: false
        }
      ]
    }
  }

}
</script>


