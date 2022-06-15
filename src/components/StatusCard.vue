<template>
  <div class="card">
    <div class="card-header text-center bg-secondary text-white">
      <h4>Neue Aufgaben</h4>
    </div>
    <div class="card-body">
      <TaskEntry />
    </div>
    <div class="card-footer">
      <NewTask />
    </div>
  </div>
</template>

<script>
import TaskEntry from "@/components/TaskEntry";
import NewTask from "@/components/NewTask";
export default {
  name: "StatusCard",
  components: {NewTask, TaskEntry},
}
</script>

<style scoped>

</style>