<template>
  <div class="Homepage">
    <ItemComponent @onTaskAdded="addTask"/>
    <ItemList :tasks="tasks" @onTaskDeleted="deleteTask"/>
  </div>
  <!-- <ItemComponent message="DataItemList" /> -->
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import * as ItemComponent from "./components/Items/ItemsComponent.vue";
import * as ItemList from "./components/Items/ItemsList.vue";
import Task from "./types/Task";

export default defineComponent({
  name: "App",
  components: {
    ItemComponent, ItemList
  },
  setup() {
    const tasks = ref<Task[]>([
      { id: "1", name: "Coffee", completed: false },
      { id: "2", name: "Read", completed: false },
      { id: "3", name: "Play", completed: false },
    ]);

    const addTask = (task: Task) => 
    {
      tasks.value.push(task);
    }

    const deleteTask = (taskID: string) => {
      console.log("delted note",taskID);
      tasks.value = tasks.value.filter(task => task.id !== taskID)
    }

    return { tasks, addTask, deleteTask};
  },
});
</script>

<style scoped>
.Homepage {
  margin: auto;
  height: auto;
  margin-top: 30px;
  display: block;
  border: 3px solid black;
  min-width: 720px;
  max-width: 720px;
  border: 1px solid white;
  border-color: rgba(255, 255, 255, 0.75);
  border-radius: 0.8em;
  -moz-border-radius: 0.8em;
  -webkit-border-radius: 0.8em;
  box-shadow: 0 0 4px rgba(50, 50, 50, 0.5);
  -moz-box-shadow: 0 0 4px rgba(50, 50, 50, 0.5);
  -webkit-box-shadow: 0 0 4px rgba(50, 50, 50, 0.5);
  padding: 0.5em;
}
</style>
