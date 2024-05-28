<script>
  export let tasks = [];

  let editedId = 0;

  const setEditedId = (id) => {
    console.log("clicked id: ", id);

    const task = tasks.find((task) => task.id === id);

    console.log("task: ", task);

    if (!task.isComplete) {
      editedId = id;
    }
  };
</script>

<div class="todo-list">
  <ul class="todo-ul">
    {#each tasks as task}
      <li class={task.isComplete ? "todo-li-complete" : "todo-li"}>
        <input
          type="checkbox"
          checked={task.isChecked}
          disabled={task.isComplete}
          on:change={() => {
            task.isChecked = !task.isChecked;
            tasks = [...tasks];
          }}
        />
        {#if task.id === editedId}
          <input
            type="text"
            bind:value={task.text}
            on:blur={() => {
              editedId = 0;
            }}
          />
        {:else}
          <span on:click={setEditedId(task.id)}>{task.text}</span>
        {/if}
      </li>
    {/each}
  </ul>
</div>

<style lang="scss" tpye="text/scss">
  .todo-list {
      margin-top: 20px;
      .todo-ul {
        padding: 0;
        margin: 0;
      }
      .todo-li,
      .todo-li-complete {
        padding: 10px 0;
        list-style: none;
        border-bottom: 1px solid #e0e0e0;
      }
      .todo-li-complete {
        text-decoration: line-through;
      }
    }
</style>
