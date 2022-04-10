<template>
  <div class="container">
    <h1 class="title">My Todo App</h1>
    <div>
      <AddTodoForm :RefreshTasks="RefreshTasks">

      </AddTodoForm>
    </div>
    <div style="background-color: #ececec; padding: 20px">
      <a-card title="My todo tasks list" style="text-align: left; gutter: 16">
          <li v-for="(item, index) in items" :key="item.id">
            <TaskCard :RefreshTasks="RefreshTasks"
              :description="item.description"
              :id="item.id"
              :index="index"
              :title="item.title"
              :isCompleted="item.is_completed"
            ></TaskCard>
          </li>
      </a-card>
    </div>
  </div>
</template>

<script>
import TaskCard from "@/components/TaskCardGrid";
import AddTodoForm from "@/components/AddTodoForm";

export default {
  name: "TodoApp",
  props: {
    msg: String,
  },

  components: {
    AddTodoForm,
    TaskCard,
  },
  methods:{
    RefreshTasks(){
      fetch("http://localhost:8000/todo")
          .then((response) => response.json())
          .then((data) => {
            console.log(data);
            this.items = data;
          });
    }
  },
  data() {
    fetch("http://localhost:8000/todo")
      .then((response) => response.json())
      .then((data) => {
        console.log(data);
        this.items = data;
      });

    return {
      parentMessage: "Parent",
      title: "",
      items: [],
    };
  }
};
</script>

<style scoped>
.title {
  text-align: center;
  margin-top: 5pt;
}
</style>
