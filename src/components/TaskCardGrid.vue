<template>
  <a-card-grid
    style="width: 25%; margin-outside: 80px; text-align: center; span: 8"
    :hoverable="true"
  >
    <div>
      <h3>{{ title }}</h3>
      <p>
        {{ description }}
      </p>
      <a-checkbox type="checkbox" value="{{isCompleted}}"> </a-checkbox>
    </div>
    <div>
      <a-button class="primary button" type="primary" shape="round"
        >view</a-button
      >
      <a-button type="primary" shape="round" @click="DeleteTask" danger>delete</a-button>
    </div>
  </a-card-grid>
</template>

<script>
export default {
  name: "TaskCard",
  props: {
    title: String,
    description: String,
    id: Number,
    index: Number,
    isCompleted: Boolean,
    RefreshTasks: Function,
  },
  methods:{
    DeleteTask(){
      fetch(`http://localhost:8000/todo/${this.id}/`, {
        method: "DELETE",
      })
          .then((data) => {
            console.log(data);
            this.RefreshTasks();
          });

    }
  }
};
</script>
