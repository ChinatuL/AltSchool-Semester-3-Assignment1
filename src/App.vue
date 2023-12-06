<template>
    <TasksHeader />
    <main class="main">
        <TasksForm />
        <TaskList />
    </main>
</template>

<script>
import TasksHeader from "./components/TasksHeader.vue";
import TasksForm from "./components/TasksForm.vue";
import TaskList from "./components/TaskList.vue";
export default {
    name: "App",
    components: {
        TasksHeader,
        TasksForm,
        TaskList,
    },
};
</script>

<style>
body {
    display: flex;
    flex-direction: column;
    width: 100%;
    min-height: 100vh;
    background: #eef2ff;
    color: #1e1b4b;
    font-family: "Montserrat", sans-serif;
}
</style>

<style scoped>
.main {
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 80%;
    max-width: 600px;
    margin: 3rem auto;
}
</style>