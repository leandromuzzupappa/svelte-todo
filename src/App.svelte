<script>
  import TodoForm from "./TodoForm.svelte";
  let todos = localStorage.getItem("todos")
    ? JSON.parse(localStorage.getItem("todos"))
    : [];
  function addTodo(todo) {
    todos.push({
      title: todo,
      done: false,
    });
    todos = todos;
  }
  function removeTodo(index) {
    todos.splice(index, 1);
    todos = todos;
  }

  $: localStorage.setItem("todos", JSON.stringify(todos));
</script>

<main>
  <h1>Hello!</h1>
  <TodoForm {addTodo} />

  <ul>
    {#each todos as { title, done }, i}
      <li class:done>
        {#if done}
          <span>🌈</span>
        {/if}
        <span on:click={() => (done = !done)}>
          {title}
        </span>
        <span class="delete" on:click={() => removeTodo(i)}> 🗑 </span>
      </li>
    {/each}
  </ul>
</main>

<style>
  .done {
    text-decoration: line-through;
  }

  .delete {
    display: inline-block;
  }
  .delete:hover {
    transform-origin: left center;
    transform: scale(1.5);
  }
</style>
