<template>
  <div class="alert" :class="alertClass">
    {{ content }}
  </div>
</template>

<script>
export default {
  name: "TaskEntry",
  props: {
    content: String,
    alertColor: {
      type: String,
      default: "secondary",
    }
  },
  computed: {
    alertClass() {
      return `alert-${this.alertColor}`;
    }
  }
}
</script>

<style scoped>

</style>