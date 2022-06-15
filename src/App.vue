<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-4" v-for="statusCard in statusCards" :key="statusCard.status">
        <StatusCard @new-task="addTask" :title="statusCard.title" :tasks="filteredTasks(statusCard.status)" :titleClasses="statusCard.titleClasses" :newTasks="statusCard.newTasks" :status="statusCard.status" />
      </div>
    </div>
  </div>
</template>

<script>
import StatusCard from "@/components/StatusCard";
export default {
  name: "App",
  components: {StatusCard},
  data() {
    return {
      tasks: [
        {
          id: 1,
          content: "Dashboard überarbeiten.",
          status: 0,
        },
        {
          id: 2,
          content: "Anwendung auf Vue.js umstellen.",
          status: 1,
        },
      ],
      statusCards: [
        {
          title: "Neue Aufgaben",
          titleClasses: "bg-secondary",
          newTasks: true,
          status: 0,
        },
        {
          title: "In Bearbeitung",
          titleClasses: "bg-primary",
          newTasks: false,
          status: 1,
        },
        {
          title: "Erledigt",
          titleClasses: "bg-success",
          newTasks: false,
          status: 2,
        },
      ],
    };
  },
  methods: {
    filteredTasks(status) {
      return this.tasks.filter((task) => task.status === status);
    },
    addTask(task) {
      task.id = this.tasks.length;
      this.tasks.push(task)
    }
  },
};
</script>

<style>
@import "~bootstrap/dist/css/bootstrap.min.css";
</style>
