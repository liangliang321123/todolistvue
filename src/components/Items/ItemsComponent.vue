<template>
  <div class="Homepage-content">
    <h1>To Do List</h1>
    <div class="HomePage-header">
      <form>
        <input type="text" v-model="newTask" placeholder="Add Task" />
        <button class="standard-button" @click.prevent="handleAddTask">
          Add Task
        </button>
      </form>
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineEmits, ref } from "vue";
import Task from "../../types/Task";

const emit = defineEmits(["onTaskAdded"]);
const newTask = ref("");

const handleAddTask = () => {
  if (newTask.value.trim() === "") {
    alert("Task name cannot be empty");
    return;
  }

  const task: Task = {
    id: Date.now().toString(),
    name: newTask.value,
    completed: false,
  };

  emit("onTaskAdded", task);
  newTask.value = "";
};

// export default defineComponent({
//   setup() {
//     //emit
//     const emit = defineEmits(["onTaskAdded"]);
//     const newTask = ref("");

//     const handleAddTask = () => {
//       console.log("addedd");
//       if (newTask.value === "") {
//         alert("Task cannot be empty");
//         return;
//       }

//       const task: Task= {
//         id: Date.now().toString(),
//         name: newTask.value,
//         completed: false,
//       };

//       emit("onTaskAdded", task);
//       newTask.value = "";
//     };
//     return { handleAddTask, newTask };
//   },
// });
</script>

<style scoped>
.Homepage-content {
  color: black;
}

.Homepage-content input {
  width: 40%;
}

.HomePage-header {
  padding: 0px;
  display: flex;
  justify-content: normal;
  align-items: center;
  font-size: 12px;
  width: 100%;
}

</style>
