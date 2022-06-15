<template>
  <div class="alert alert-secondary">
    {{ content }}
  </div>
</template>

<script>
export default {
  name: "TaskEntry",
  props: {
    content: String,
  }
}
</script>

<style scoped>

</style>