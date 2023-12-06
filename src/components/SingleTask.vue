<template>
    <div class="task">
        <div class="task-left">
            <input
                type="checkbox"
                :checked="task.completed"
                v-on:change="markAsDone"
            />
            <input
                class="text-input"
                v-bind:class="{ completed: task.completed }"
                v-bind:disabled="!isEditing"
                v-model="task.title"
                v-on:keyup.enter="updateTask"
            />
        </div>
        <div class="task-right">
            <button>
                <i class="fas fa-edit green" @click="isEditing = true"></i>
            </button>
            <button>
                <i class="fas fa-trash red" @click="deleteTask(task.id)"></i>
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: "SingleTask",
    props: {
        initialTask: {
            type: Object,
            required: true,
        },
    },
    data() {
        return {
            task: { ...this.initialTask },
            isEditing: false,
        };
    },
    methods: {
        updateTask() {
            this.$store.commit("updateTask", {
                id: this.task.id,
                completed: this.task.completed,
                title: this.task.title,
            });
            this.isEditing = false;
        },
        deleteTask(id) {
            this.$store.commit("deleteTask", { id });
        },
        markAsDone() {
            this.task.completed = !this.task.completed;
            this.$store.commit("updateTask", {
                id: this.task.id,
                completed: this.task.completed,
                title: this.task.title,
            });
        },
    },
};
</script>

<style scoped>
.task {
    display: grid;
    grid-template-columns: auto auto;
    gap: 1rem;
}

.task-left,
.task-right {
    display: flex;
    align-items: center;
    gap: 1rem;
}

.task-right button {
    cursor: pointer;
    transition: all 0.3s ease-in-out;
}

.task-right button:hover {
  transform: scale(1.1);
}

input[type="checkbox"] {
    accent-color: #1e1b4b;
    cursor: pointer;
}

.text-input {
    width: 100%;
}

.text-input:not(:disabled) {
    background: #fbfbfc;
    border: 1px solid #bfdbfe;
    padding: 0.2rem;
}

.text-input:not(:disabled):focus, .text-input:not(:disabled):active {
     outline: 1px solid #3b82f6;
    outline-offset: 2px;
}

input.completed {
    text-decoration: line-through;
    color: #1e1b4b;
}
</style>
