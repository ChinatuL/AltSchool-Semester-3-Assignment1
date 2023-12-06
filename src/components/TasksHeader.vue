<template>
    <header class="header">
        <h1>
            Task<span>Zen</span>
        </h1>
        <div class="statistics">
            {{ totalCompletedTasks }} / {{ totalTasks }} Completed Tasks
        </div>
    </header>
</template>

<script>
import { mapGetters } from "vuex";
export default {
    name: "TasksHeader",
    computed: {
        ...mapGetters(["totalTasks", "totalCompletedTasks"]),
    },
};
</script>

<style scoped>
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 80%;
    max-width: 700px;
    margin: 0 auto;
    padding: 2rem 0;
}
.header h1 {
    font-weight: 700;
    font-size: 2rem;
}

.header span {
  color: #4f46e5;
}

.statistics {
  font-weight: 500;
  font-size: 1.5rem;
}

@media (max-width: 640px) {
    .header {
        flex-direction: column;
        align-items: flex-start;
        padding: 2rem;
        margin: 0;
        gap: 1rem;

    }

    .statistics {
        font-size: 1rem;
    }
}
</style>
