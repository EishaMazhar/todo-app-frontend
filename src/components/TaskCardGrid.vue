<template>
  <a-card-grid
      style="width: 25%; margin-outside: 80; text-align: center; span: 8; background-color: burlywood"
      :hoverable="true"
  >
    <div>
      <div>
        <span>
          <a-checkbox style="margin: 10px" type="checkbox" :checked="isCompleted" @change="UpdateTask" /><h3>{{ title }}</h3>
        </span>
        <p class="text-black-50"><i>created on: {{ created_on }}</i></p>
      </div>
      <p>
        {{ description }}
      </p>

    </div>
    <div>

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
    created_on: Date,
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


    UpdateTask(event) {
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
