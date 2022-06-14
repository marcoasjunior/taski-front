<template>
  <div>
    <CreateTaskForm />
  </div>
</template>

<script>
import CreateTaskForm from "../components/CreateTaskForm.vue";
export default {
  name: "TasksView",
  components: {
    CreateTaskForm,
  },
};
</script>
