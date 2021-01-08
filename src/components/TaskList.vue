<template>
    <div class="container">
        <div class="wrapper">
            <div class="section-box">
                <h1>To Do List</h1>
            </div>
            <div class="task-list">
                <table>
                    <tr v-if="tasks.length">
                        <th class="table-head">Done?</th>
                        <th class="table-head">Task itself</th>
                    </tr>
                    <tr v-for="task in tasks" :key="task.taskID">
                        <td class="task-check-box">
                            <input :id="task.taskID" type="checkbox" />
                        </td>
                        <td class="task-content">
                            <label :for="task.taskID">{{
                                task.taskName
                            }}</label>
                        </td>
                    </tr>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        tasks: Array,
    },
    methods: {},
    data() {
        return {};
    },
};
</script>

<style scoped lang="scss">
.container {
    color: var(--accent-white);
    font-family: var(--text-font);
    font-size: 5vw;

    display: flex;
    align-items: flex-start;
    justify-content: center;
    width: 100%;
    height: 100vh;
    .wrapper {
        width: 90%;
        .section-box {
            h1 {
                margin: 0;
            }
        }
        .task-list {
            table {
                width: 100%;
            }
            .table-head {
                color: var(--accent-blue);
            }
            .task-content {
                width: 90%;
            }
            .task-check-box {
                width: 10%;
                input {
                    width: 3vw;
                    height: 3vw;
                    border-radius: 32px;
                }
            }
        }
    }
}
</style>
