<template>
  <div>
    <a-form
        name="basic"
        :label-col="{ span: 8 }"
        :wrapper-col="{ span: 16 }"
        autocomplete="off"
    >
      <a-form-item
          label="Title"
          name="title"
          :rules="[
                { required: true, message: 'Please input your task title!' },
              ]"
      >
        <a-input v-model:value="newTitle" style="width: fit-content"/>
      </a-form-item>

      <a-form-item
          label="Description"
          name="description"
      >
        <a-textarea v-model:value="newDescription" placeholder="Description" :rows="1" style="width: max-content"/>
      </a-form-item>


      <a-form-item :wrapper-col="{ offset: 8, span: 16 }">
        <a-button @click="newTask" type="primary" html-type="submit"
        >Create new task
        </a-button
        >
      </a-form-item>
    </a-form>
  </div>
</template>
<script>
export default {
  name: "AddTodoForm",
  props: {
    msg: String,
    RefreshTasks: Function,

  },


  methods: {
    newTask() {
      fetch("http://localhost:8000/todo/", {
        method: "POST",
        headers: {
          Accept: "application/json",
          "Content-Type": "application/json",
        },
        body: JSON.stringify({title: this.newTitle, description: this.newDescription, is_completed: false}),
      })
          .then((response) => response.json())
          .then((data) => {
            console.log(data);
            this.RefreshTasks()
          });

    }
  }
}
</script>