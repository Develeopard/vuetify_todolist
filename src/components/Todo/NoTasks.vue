<template>
    <div
      class="no-tasks"
    >
    <v-icon
      size="100"
      color="green darken-2"
    >
      mdi-check
    </v-icon>

    <div class="text-h5 primary--text">No Tasks</div>
    </div>
</template>


<style lang="scss">
  .no-tasks{
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    opacity: .5;
  }  
</style>