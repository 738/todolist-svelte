<script>
  let inputValue = "";
  let todos = [];
  function addTodo() {
    if (inputValue === "") alert("입력하세요!");
    todos = [
      ...todos,
      {
        contents: inputValue,
        completed: false
      }
    ];
    inputValue = "";
  }
  function toggleTodo(i) {
    todos = [
      ...todos.slice(0, i),
      {
        ...todos[i],
        completed: !todos[i].completed
      },
      ...todos.slice(i + 1)
    ];
  }
</script>

<style>
  li.completed {
    text-decoration: line-through;
    color: #e4e4e4;
  }
</style>

<input type="text" bind:value={inputValue} />
<button on:click={addTodo}>추가</button>

<ul>
  {#each todos as todo, i}
    <li
      on:click={() => toggleTodo(i)}
      class={todo.completed ? 'completed' : ''}>
      {todo.contents}
    </li>
  {/each}
</ul>
