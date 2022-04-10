<template>
  <div class="container">
    <div>
      <h1 class="title">My Todo App</h1>
      <TaskCard></TaskCard>
    </div>
  </div>
</template>

<script>
import TaskCard from "@/components/TaskCardGrid";

export default {
  name: 'TodoApp',
  props: {
    msg: String
  },
  components:{
    TaskCard
  },
}
</script>

<style scoped>
.title {
  text-align: center;
  margin-top: 5pt;
}
</style>