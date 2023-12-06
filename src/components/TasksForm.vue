<template>
    <div class="form-control">
        <input
            type="text"
            id="task-input"
            v-model="title"
            v-on:keyup.enter="addTask"
            placeholder="Add a new task..."
        />
        <button
            class="add-btn"
            id="butAdd"
            v-on:click="addTask"
        >
            <i class="fa-solid fa-plus"></i>
        </button>
    </div>
</template>

<script>
export default {
    name: "TasksForm",
    data() {
        return {
            title: "",
        };
    },
    methods: {
        addTask() {
            if (this.title.trim() === "") {
                return;
            }
            this.$store.commit("addTask", {
                title: this.title,
                completed: false,
                id: this.$store.state.tasks.length + 1,
            });
            this.title = "";
        },
    },
};
</script>

<style scoped>
.form-control {
    display: flex;
    gap: 1rem;
    align-items: center;
    margin-bottom: 1rem;
}

.form-control input {
    width: 80%;
    padding: 0.5rem;
    background: #fbfbfc;
    border: 1px solid #bfdbfe;
    border-radius: 5px;
    font-size: 0.9rem;
    font-family: "Montserrat", sans-serif;
}

.form-control input:focus,
.form-control input:active {
    outline: 1px solid #3b82f6;
    outline-offset: 2px;
}

.add-btn {
  border: 1px solid #1e1b4b;
  padding: 0.1rem 0.4rem;
  border-radius: 50%;
  transition: all 0.3s ease-in-out;
}
.add-btn:hover {
  transform: scale(1.1);
}
</style>
