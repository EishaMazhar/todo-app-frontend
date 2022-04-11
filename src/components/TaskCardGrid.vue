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

    </div>
    <div>
      <a-checkbox type="checkbox" :checked="isCompleted" @change="UpdateTask"></a-checkbox>
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
  methods: {
    DeleteTask() {
      fetch(`http://localhost:8000/todo/${this.id}/`, {
        method: "DELETE",
      })
          .then((data) => {
            console.log(data);
            this.RefreshTasks();
          });

    },


  UpdateTask(event){
    console.log(event)
    fetch(`http://localhost:8000/todo/${this.id}/`, {
      method: "PATCH",
      headers: {
        Accept: "application/json",
        "Content-Type": "application/json",
      },
      body: JSON.stringify({is_completed: event.target.checked}),
    })
        .then((response) => response.json())
        .then((data) => {
          console.log(data);
          this.RefreshTasks()
        });

  }
  }
};
</script>
