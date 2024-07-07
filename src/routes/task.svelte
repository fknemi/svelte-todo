<script>
    export let id;
    export let title;
    export let completed;
</script>

<div class={`task ${completed ? "checked" : ""}`}>
    <div class="checkbox">
        <input type="checkbox" {id} bind:checked={completed} />
        <label for={id}></label>
    </div>
    <span>{title}</span>
</div>

<style>
    .task {
        display: flex;
        align-items: center;
        justify-content: space-between;
        font-size: 1.5rem;
        gap: 2rem;
    }

    .checkbox {
        width: 2rem;
        height: 2rem;
        background-color: #f4f4f4;
        border: 2px solid rgba(0, 0, 0, 0.4);
        border-radius: 8px;
        display: inline-flex;
        position: relative;
        justify-content: center;
        align-items: center;
        overflow: hidden;
        transition:
            box-shadow 0.3s,
            transform 0.3s;
    }

    .checkbox input[type="checkbox"] {
        cursor: pointer;
        width: 100%;
        height: 100%;
        border: none;
        outline: none;
        -webkit-appearance: none;
        -moz-appearance: none;
        appearance: none;
        position: absolute;
        top: 0;
        left: 0;
        opacity: 0;
    }

    .checkbox label {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 80%;
        height: 80%;
        background-color: transparent;
        border-radius: inherit;
        border: 2px solid transparent;
    }

    .checkbox:hover {
        box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.2);
        transform: scale(1.05);
    }

    .checkbox input[type="checkbox"]:checked {
        text-decoration: line-through;
        color: rgba(0, 0, 0, 0.4);
    }
    .checked span {
        text-decoration: line-through;
        color: rgba(0, 0, 0, 0.4);
    }

    .checkbox input[type="checkbox"]:checked + label::after {
        content: "";
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 50%;
        height: 50%;
        border-bottom: 3px solid #000;
        border-right: 3px solid #000;
        opacity: 0.7;
    }
</style>
