<template>
  <div class="home">
    <list-tasks 
    v-if="$store.state.tasks.length" 
    />
    
    <no-tasks
    v-else
    />
    <done-sorting
    v-if="$store.state.sorting"
    />

  </div>
</template>

<script>
export default {
  name: "Home",

  components: {
    "list-tasks": require("@/components/ToDo/ListTasks.vue").default,
    "no-tasks": require("@/components/ToDo/NoTasks.vue").default,
    "done-sorting": require("@/components/ToDo/Dialogs/DoneSorting.vue").default,
  },
};
</script>
