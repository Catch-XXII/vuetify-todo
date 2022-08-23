<template>
   <v-dialog
        ref="dialog"
        :value="true"
        :return-value.sync="date"
        persistent
        width="290px"
      >
        <v-date-picker
          v-model="date"
          scrollable
        >
          <v-spacer></v-spacer>
          <v-btn
            @click="$emit('close')"
            text
            color="primary"

          >
            Cancel
          </v-btn>
          <v-btn
            @click="changeDueDate"
            text
            color="primary"
          >
            OK
          </v-btn>
        </v-date-picker>
      </v-dialog>
</template>

<script>
export default {
    data(){
        return {
            date: null
        }
    },

 props: ["task"],
 mounted(){
    if (this.task.dueDate) {
        this.date = this.task.dueDate
    }
 },
 methods:{
    changeDueDate(){
        let payload = {
            id: this.task.id,
            dueDate: this.date
        }
        this.$store.dispatch('updateTaskDueDate', payload)
        this.$emit("close");
    }
 }
}
</script>
