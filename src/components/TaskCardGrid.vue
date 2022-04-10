<template>
  <div style="background-color: #ececec; padding: 20px">
    <a-card title ='My todo tasks list' style="text-align: left; gutter: 16">
      <a-card-grid style="width: 25%; margin-outside: 80px;text-align: center; span: 8" :hoverable="true">
        <div>
          <h3>complete the todo app</h3>
        </div>
        <div>
          <a-button class="primary button" type='primary' shape="round">view</a-button>
          <a-button type='primary' shape="round" danger>delete</a-button>
        </div>
      </a-card-grid>
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