<template>
  
    <v-dialog
    :value=true
    
      max-width="290"
    >
      <v-card>
        <v-card-title class="text-h5">
          Delete Task?
        </v-card-title>

        <v-card-text>
          Are you sure you want to delete the task?
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn
            @click="$emit('close')"
            text
          >
            No
          </v-btn>

          <v-btn
            @click="$store.dispatch('deleteTask', task.id)"
            color="red darken-1"
            text
          >
            Yes
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</template>

<script>
export default {
props: ['task']
}
</script>
