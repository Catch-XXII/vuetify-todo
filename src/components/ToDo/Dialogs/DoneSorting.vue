<template>
  <v-btn
  @click="$store.commit('toggleSorting')"
  color="primary"
  class="done-sorting"
  >
    Done Sorting
  </v-btn>
</template>

<script>
export default {

}
</script>

<style lang="sass">
.done-sorting
  position: fixed
  bottom: 20px
  left: 50%
  transform: translate(-50%)

</style>