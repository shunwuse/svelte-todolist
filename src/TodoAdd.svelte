<script>
  import { createEventDispatcher } from "svelte";

  export let tasks = [];
  let text = "";

  const dispatch = createEventDispatcher();

  const addTask = () => {
    if (text.length <= 0) {
      alert("Please enter task");
      return;
    }

    const newTask = {
      id: tasks.length + 1,
      text: text,
      isChecked: false,
      isComplete: false,
    };

    dispatch("updateTasks", [...tasks, newTask]);

    text = "";
  };
</script>

<div class="todo-add-area">
  <input
    class="todo-add-input"
    bind:value={text}
    type="text"
    placeholder="Add new task"
  />
  <button class="todo-add-button" on:click={addTask}>Add</button>
</div>

<style lang="scss" tpye="text/scss">
  .todo-add-area {
    display: flex;

    .todo-add-input {
      flex: 0;
      min-width: 200px;
    }
    .todo-add-button {
      flex: 0;
      min-width: 80px;
    }
  }
</style>
