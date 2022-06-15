<template>
  <div class="card">
    <div class="card-header text-center text-white" :class="titleClasses">
      <h4>{{ title }}</h4>
    </div>
    <div class="card-body" v-for="task in tasks" :key="task.id">
      <TaskEntry :content="task.content" :alert-color="alertColor"/>
    </div>
    <div v-if="tasks.length === 0">
      <div class="card-body">
        <div class="alert alert-secondary">
          Es gibt im Moment keine Aufgaben hier!
        </div>
      </div>
    </div>
    <div class="card-footer" v-if="newTasks">
      <NewTask @new-task="newTask" />
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
  },
  emits: {
    "new-task": (task) => {
      if (!("status" in task)) {
        console.warn("Jede Aufgabe muss ein Status-Attribut haben.");
        return false;
      }
      return true;
    }
  },
  computed: {
    alertColor() {
      switch (this.status) {
        case 0: return "secondary"
        case 1: return "primary"
        case 2: return "success"
        default: return "danger"
      }
    },
  },
  methods: {
    newTask(task) {
      task.status = this.status;
      this.$emit("new-task", task);
    }
  }
}
</script>

<style scoped>

</style>