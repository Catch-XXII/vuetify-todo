<template>
  <div id="no-tasks"
      class="no-tasks"
      
    >
      <v-icon
        size="100"
        color="primary"
      >
        mdi-check
      </v-icon>
      <div id='no-tasks' class="text-h5 primary--text">No tasks</div>
    </div>
</template>


<style lang="sass">
.no-tasks
  position: absolute
  left: 50%
  top: 50%
  transform: translate(-50%, -50%)
  opacity: 0.5
</style>