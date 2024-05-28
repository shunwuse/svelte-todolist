<script>
  import TodoAdd from "./TodoAdd.svelte";
import TodoList from "./TodoList.svelte";
  import TodoTotal from "./TodoTotal.svelte";

  let tasks = [
    { id: 1, text: "Task 1", isChecked: false, isComplete: false },
    { id: 2, text: "Task 2", isChecked: true, isComplete: true },
    { id: 3, text: "Task 3", isChecked: false, isComplete: false },
  ];

  const updateTasks = (e) => {
    tasks = e.detail;
  };
</script>

<div class="todo">
  <div class="todo-header">TODO LIST</div>

  <TodoList {tasks} />

  <TodoTotal {tasks} on:updateTasks={updateTasks} />

  <TodoAdd {tasks} on:updateTasks={updateTasks} />
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
  }
</style>
