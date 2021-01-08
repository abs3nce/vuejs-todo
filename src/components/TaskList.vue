<template>
    <div class="container">
        <div class="wrapper">
            <div class="section-box">
                <h1>To Do List</h1>
            </div>
            <div class="task-list">
                <h1 v-if="tasks.length == 0">You have no tasks right now!</h1>
                <table>
                    <tr v-if="tasks.length">
                        <th class="table-head">Done?</th>
                        <th class="table-head">Task itself</th>
                        <th class="table-head">Rewrite</th>
                        <th style="color: #ff6666">Scrap it!</th>
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

                        <td>
                            <button
                                class="task-rewrite-button"
                                :id="task.taskID"
                            >
                                <img
                                    src="https://img.icons8.com/ios/50/000000/pencil-tip.png"
                                />
                            </button>
                        </td>

                        <td>
                            <button
                                class="task-delete_button"
                                :id="task.taskID"
                                @click="removeTask(task.taskID)"
                            >
                                <img
                                    src="https://img.icons8.com/flat_round/64/000000/delete-sign.png"
                                />
                            </button>
                        </td>
                    </tr>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    methods: {
        removeTask(taskID) {
            this.$emit("remove:task", taskID);
        },
    },
    props: {
        tasks: Array,
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
                width: 50%;
            }
            .task-check-box {
                width: 10%;
                input {
                    width: 3vw;
                    height: 3vw;
                    border-radius: 32px;
                }
            }
            .task-rewrite-button {
                background: none;
                border: none;
            }
            .task-rewrite-button:focus {
                outline: none;
            }
            .task-delete_button {
                background: none;
                border: none;
            }
            .task-delete_button:focus {
                outline: none;
            }
        }
    }
}
</style>
