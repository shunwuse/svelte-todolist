<script>
  import { createEventDispatcher } from "svelte";

  export let tasks = [];

  const dispatch = createEventDispatcher();

  const doneTask = () => {
    console.log("done: ", tasks);

    tasks = tasks.map((task) => {
      if (task.isChecked) {
        task.isComplete = true;
      }

      console.log("done tasks: ", tasks);

      dispatch("updateTasks", tasks);
    });
  };

  const deleteTask = () => {
    tasks = tasks.filter((task) => !task.isChecked || task.isComplete);

    console.log("delete tasks: ", tasks);

    dispatch("updateTasks", tasks);
  };

  $: countNotComplete = tasks.filter((task) => !task.isComplete).length;
</script>

<div>
  [<span
    class="todo-done"
    on:click={doneTask}
  >
    Done
  </span>]
  &nbsp;
   [<span
    class="todo-delete"
    on:click={deleteTask}
  >
    Delete
  </span>]
</div>

<div class="todo-total">
  Total Task: {tasks.length}, Not Complate: {countNotComplete}
</div>

<style lang="scss" tpye="text/scss">
  .todo-done {
    cursor: pointer;
    color: blue;
  }

  .todo-delete {
    cursor: pointer;
    color: red;
  }

  .todo-total {
    padding: 10px 0;
  }
</style>
