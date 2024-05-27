<script>
</script>

<div class="todo">
  <div class="todo-header">TODO LIST</div>

  <div class="todo-list">
    <ul class="todo-ul">
      <li class="todo-li">
        <input type="checkbox" />
        <span>Task 1</span>
      </li>
    </ul>
  </div>

  <div class="todo-total">Total Task: 4, Not Complate: 0</div>

  <div class="todo-add-area">
    <input class="todo-add-input" type="text" placeholder="Add new task" />
    <button class="todo-add-button">Add</button>
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

    .todo-list {
      margin-top: 20px;
      .todo-ul {
        padding: 0;
        margin: 0;
      }
      .todo-li {
        padding: 10px 0;
        list-style: none;
        border-bottom: 1px solid #e0e0e0;
      }
    }

    .todo-total {
      padding: 10px 0;
    }

    .todo-add-area {
      display: flex;

      .todo-add-input  {
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
