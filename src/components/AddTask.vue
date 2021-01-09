<template>
    <div class="container">
        <div class="wrapper">
            <div class="section-box">
                <h1 class="greeting">Hello {{ userName }}!</h1>
            </div>
            <div class="task-input">
                <input
                    class="input-box"
                    type="text"
                    placeholder="Write your task here"
                    v-model="taskName"
                />
                <button class="submit-button" @click.prevent="addTask">
                    Add it!
                </button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {},
    methods: {
        addTask() {
            this.$emit("add:task", {
                taskName: this.taskName,
            });
            this.taskName = "";
        },
    },
    data() {
        return {
            userName: "Jakub",
            taskName: "",
        };
    },
};
</script>

<style scoped lang="scss">
.container {
    color: #fff;
    font-family: "Indie Flower", cursive;
    font-size: 5vw;

    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100vh;

    .wrapper {
        width: 100%;
    }

    .section-box {
        .greeting {
            font-family: var(--h1-font);
            color: var(--accent-white);
            margin: 0;
        }
    }

    .input-box {
        font-family: var(--text-font);
        font-size: 2vw;
        width: 30%;

        background: none;

        border: none;

        vertical-align: middle;
    }
    .input-box:focus {
        outline: none;
    }
    .input-box::placeholder {
        color: var(--accent-blue);
    }

    .submit-button {
        width: 15%;
        text-align: center;
        vertical-align: middle;
        margin-left: 32px;

        background-color: var(--accent-blue);
        font-family: var(--text-font);
        font-size: 2vw;

        border: 1px solid var(--accent-blue);
        border-radius: 32px;

        display: inline-block;
        cursor: pointer;
        text-align: center;
        outline: none;
    }
    .submit-button:hover {
        background-color: var(--accent-blue-light);
        border: 1px solid var(--accent-blue-light);
    }
    .submit-button:active {
        background-color: var(--accent-purple);
        border: 1px solid var(--accent-purple);
        transform: translateY(2px);
    }
}
</style>
