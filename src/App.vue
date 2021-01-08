<template>
    <div id="app">
        <add-task @add:task="addTask" />
        <task-list :tasks="tasks" @remove:task="removeTask" />
    </div>
</template>

<script>
import AddTask from "./components/AddTask.vue";
import TaskList from "./components/TaskList.vue";

export default {
    data() {
        return {
            tasks: [],
        };
    },
    methods: {
        addTask(task) {
            this.tasks.push({
                taskName: task.taskName,
                taskDone: false,
                taskID: this.tasks.length,
            });
        },

        removeTask(taskID) {
            console.log(taskID);
            this.tasks.splice(taskID, 1);

            this.tasks = this.tasks.map((value, index) => {
                value.taskID = index;
                return value;
            });
        },
    },
    name: "App",
    components: {
        TaskList,
        AddTask,
    },
};
</script>

<style lang="scss">
:root {
    --background-color: #ffd5cd;
    --background-color-darker: #efbbcf;
    --accent-white: #f5f5f5;
    --accent-blue: #c3aed6;
    --accent-purple: #8675a9;
    --h1-font: "Amatic SC", cursive;
    --text-font: "Amatic SC", cursive;
}

//FONTS IMPORT
@import url("https://fonts.googleapis.com/css2?family=Lobster&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Permanent+Marker&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Amatic+SC:wght@700&display=swap");

body {
    margin: 0;
    padding: 0;

    // background-color: var(--background-color);
    background: -webkit-linear-gradient(bottom right, #ffd5cd, #efbbcf);
    background: -moz-linear-gradient(bottom right, #ffd5cd, #efbbcf);
    background: linear-gradient(to bottom right, #ffd5cd, #efbbcf);
    text-align: center;
}
body::-webkit-scrollbar {
    width: 0 !important;
}
</style>
