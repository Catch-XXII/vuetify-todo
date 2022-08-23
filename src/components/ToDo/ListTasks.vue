<template>
  <v-list class="pt-0" flat>


    <draggable
    v-model="tasks"
    handle=".handle"
    >
      <task 
      v-for="task in tasks" 
      :key="task.id" 
      :task='task'

      />
     <v-divider></v-divider>
     </draggable>
  </v-list>
</template>

<script>
import draggable from 'vuedraggable'

export default {
  components: {
    task: require("@/components/ToDo/Task.vue").default,
    draggable
  },
  computed:{
    tasks:{
      get(){
        return this.$store.getters.taskFiltered
      }, 
      set(value){
          this.$store.dispatch('setTasks', value)
      }
    }
  }
};
</script>
