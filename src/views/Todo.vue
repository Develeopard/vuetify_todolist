<template>
  <div class="todo">

    <ListTasks 
      v-if="$store.state.tasks.length"
    />

    <NoTasks v-else/>

    <button-done-sorting v-if="$store.state.sorting"/>

  </div>
</template>

<script>

import ListTasks from '@/components/Todo/ListTasks';
import NoTasks from '@/components/Todo/NoTasks'

  export default {
    name: 'Todo',
    components: {

      ListTasks,
      NoTasks,
      'button-done-sorting': require('@/components/Todo/ButtonDone.vue').default //another way of adding components
    },
  }
</script>


