<template>
  <div class="todo">
    <FieldAddTask />
    <ListTasks 
      v-if="$store.state.tasks.length"
    />

    <NoTasks v-else/>

  </div>
</template>

<script>
import FieldAddTask from '@/components/Todo/FieldAddTask';
import ListTasks from '@/components/Todo/ListTasks';
import NoTasks from '@/components/Todo/NoTasks'

  export default {
    name: 'Todo',
    components: {
      FieldAddTask,
      ListTasks,
      NoTasks
    },
  }
</script>


