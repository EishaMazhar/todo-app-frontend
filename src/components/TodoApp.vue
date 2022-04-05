<template>
  <div class="container">
    <div>
      <h1 class="title">My Todo App</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoApp',
  props: {
    msg: String
  }
}

</script>

<style scoped>
.title {
  text-align: center;
  margin-top: 5pt;
}
</style>