<script>
  import TodoList from "./TodoList.svelte";

  let text = "";

  let tasks = [
    { id: 1, text: "Task 1", isChecked: false, isComplete: false },
    { id: 2, text: "Task 2", isChecked: true, isComplete: true },
    { id: 3, text: "Task 3", isChecked: false, isComplete: false },
  ];

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

    tasks = [...tasks, newTask];
    text = "";
  };

  const doneTask = () => {
    tasks = tasks.map((task) => {
      if (task.isChecked) {
        task.isComplete = true;
      }

      return task;
    });
  };

  const deleteTask = () => {
    tasks = tasks.filter((task) => !task.isChecked || task.isComplete);
  };

  $: countNotComplete = () => {
    return tasks.filter((task) => !task.isComplete).length;
  };
</script>

<div class="todo">
  <div class="todo-header">TODO LIST</div>

  <TodoList {tasks} />

  <div>
    [<span class="todo-done" on:click={doneTask}> Done </span>] &nbsp; [<span
      class="todo-delete"
      on:click={deleteTask}
    >
      Delete
    </span>]
  </div>

  <div class="todo-total">
    Total Task: {tasks.length}, Not Complate: {countNotComplete()}
  </div>

  <div class="todo-add-area">
    <input
      class="todo-add-input"
      bind:value={text}
      type="text"
      placeholder="Add new task"
    />
    <button class="todo-add-button" on:click={addTask}>Add</button>
  </div>
</div>

<style lang="scss" tpye="text/scss">
  .todo {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #f0f0f0;
    width: 350px;
    min-height: 300px;
    padding: 20px;
    border: 2px solid #e0e0e0;

    .todo-header {
      text-align: center;
      font-size: 36px;
      font-weight: 600;
    }

    .todo-total {
      padding: 10px 0;
    }
    .todo-done {
      cursor: pointer;
      color: blue;
    }
    .todo-delete {
      cursor: pointer;
      color: red;
    }

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
  }
</style>
