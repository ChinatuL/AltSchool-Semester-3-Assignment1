<template>
    <div class="tasks">
        <p v-if="totalTasks === 0">No tasks to display</p>
        <SingleTask v-for="task in tasks" :key="task.id" :initialTask="task"></SingleTask>
    </div>
</template>

<script>
import { mapGetters } from "vuex";
import SingleTask from "./SingleTask.vue";
export default {
    name: "TaskList",
    computed: {
        ...mapGetters(["tasks", "totalTasks"]),
    },
    components: {
        SingleTask,
    },
};
</script>

<style scoped>
.tasks {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
</style>