<template>
  <table class="table-form">
    <tr>
      <th>CheckList</th>
      <th>Task Name</th>
      <th>Task Completed</th>
      <th>Action</th>
    </tr>
    <tr v-for="task in tasks" :key="task.id">
      <td>
        <input
          type="checkbox"
          v-model="task.completed"
          @change="handleCompleted()"
        />
      </td>
      <td>{{ task.name }}</td>
      <td>{{ task.completed ? "Completed" : "Incomplete" }}</td>
      <td colSpan="{2}">
        <button className="standard_button">Edit</button>
        <button className="standard_button" @click.prevent="handleDeleteTask(task.id)">
          Delete
        </button>
      </td>
    </tr>
  </table>
</template>

<script setup lang="ts">
import { defineComponent, defineProps, ref, PropType, defineEmits } from "vue";
import Task from "../../types/Task";

const props = defineProps({
  tasks: {
    required: true,
    type: Array as PropType<Task[]>,
  },
});

const handleCompleted = () => {
  alert("Done");
};

const emit = defineEmits(["onTaskDeleted"]);

const handleDeleteTask = (taskID: string) => {
  emit("onTaskDeleted",taskID);
};

// export default defineComponent({
//   props: {
//     tasks: {
//       required: true,
//       type: Array as PropType<Task[]>,
//     },
//   },
//   setup() {
//     const handleCompleted = () => {
//       alert("Done");
//     };

//     const emit = defineEmits(["onTaskDeleted"]);

//     const handleDeleteTask = () => {
//         emit("onTaskDeleted");
//     }
//     return { handleCompleted, handleDeleteTask};
//   },
// });
</script>

<style scoped>
</style>
