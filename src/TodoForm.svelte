<script>
  function formSubmitted(event) {
    event.preventDefault();

    console.log("Form was submitted");
  }
</script>

<form on:submit|preventDefault={formSubmitted}>
  <label>
    New Todo
    <input type="text" placeholder="Enter a todo ..." />
  </label>
  <button>Add Todo</button>
</form>
