<template>
  <div class="card">
    <div class="card-header text-center text-white" :class="titleClasses">
      <h4>{{ title }}</h4>
    </div>
    <div class="card-body" v-for="task in tasks" :key="task.id">
      <TaskEntry :content="task.content" />
    </div>
    <div class="card-footer" v-if="newTasks">
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
  props: {
    title: String,
    titleClasses: String,
    status: Number,
    newTasks: Boolean,
    tasks: Array,
  }
}
</script>

<style scoped>

</style>