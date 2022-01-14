<script>
  export let addTodo;
  let newTodo = "";

  function formSubmitted(event) {
    addTodo(newTodo);
    newTodo = "";
  }
</script>

<form on:submit|preventDefault={formSubmitted}>
  <label>
    New Todo
    <input type="text" bind:value={newTodo} placeholder="Enter a todo ..." />
  </label>
  <button>Add Todo</button>
</form>
