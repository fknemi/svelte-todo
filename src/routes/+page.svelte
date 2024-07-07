<script>
    import Task from "./task.svelte";

    let tasks = [
        { id: "101", title: "Task #101", completed: false },
        { id: "102", title: "Task #102", completed: false },
        { id: "103", title: "Task #103", completed: false },
        { id: "104", title: "Task #104", completed: false },
        { id: "105", title: "Task #105", completed: false },
        { id: "106", title: "Task #106", completed: false },
    ];
    let taskTitle = "";

    function onSubmit(e) {
        e.preventDefault();
        if (taskTitle.trim()) {
            tasks = [
                ...tasks,
                {
                    id: Date.now().toString(),
                    title: taskTitle,
                    completed: false,
                },
            ];
            taskTitle = ""; // Clear the input after submission
        }
    }
</script>

<main>
    {#each tasks as task (task.id)}
        <Task id={task.id} title={task.title} completed={task.completed} />
    {/each}
    <input bind:value={taskTitle} on:change={onSubmit} />
</main>

<style>
    @import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@300..800&display=swap");

    *,
    *::after,
    *::before {
        font-family: "Open Sans", sans-serif;
        font-weight: 450;
        margin: 0;
        padding: 0;
        transition: all 0.5s;
    }

    :global(html, body) {
        overflow-x: hidden;
        height: 100vh;
        width: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-left: 30vh;
    }

    main {
        border-radius: 8px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;
        gap: 2rem;
    }
    input {
        width: 20rem;
        height: 2rem;
        outline: none;
        border: 2px solid #1111;
        border-radius: 8px;
        justify-self: center;
        margin-left: -10%;
    }
</style>
