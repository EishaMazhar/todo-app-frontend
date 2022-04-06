<template>
  <div style="background-color: #ececec; padding: 20px">
    <a-card title ='my todo tasks' style="text-align: left; gutter: 16">
      <a-card-grid style="width: 25%; text-align: center; span: 8" :hoverable="true"><div><h3>task 1</h3></div>Content<button></button></a-card-grid>
    </a-card>
  </div>
</template>

<script>
export default {
  name: 'TaskCard',
  props: {
    msg: String
  }
}
</script>