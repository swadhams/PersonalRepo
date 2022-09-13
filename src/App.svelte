 <script>
let todoArray = [];
let listItem = '';

function addTodo() {
	
	const todo = {
		  text: listItem,
		  checked: false,
		  id: Date.now(),
	  };
	  console.log(todoArray);
	todoArray = [...todoArray, todo];
	listItem = '';
	}	
	function toggleDone(id) {
  const index = todoArray.findIndex(item => item.id === Number(id));
  todoArray[index].checked = !todoArray[index].checked;
}
function deleteTodo(id) {
  todoArray = todoArray.filter(item => item.id !== Number(id));
}
</script>

<main>
	<div class="container">
	<h1>Todo List</h1>
	<form on:submit|preventDefault={addTodo}>
	<input class="input" type="text" placeholder="What do you want to do today?" bind:value={listItem}>
	</form>
	  </div>
	  <ul class="todo-list">
		  {#each todoArray as todo}
			<li class="todo-item {todo.checked ? 'done' : ''}">
			  <input id={todo.id} type="checkbox" />
			  <label for={todo.id} class="tick" on:click={() => toggleDone(todo.id)}></label>
			  <span>{todo.text}</span>
			  <button class="delete-todo" on:click={() => deleteTodo(todo.id)}>Delete
				</button>
			</li>
		  {/each}
		</ul>
</main>

<style>
	
main {
		text-align: center;
	}

input[type="text"]{
		width: 50%;
	}

.todo-item span {
font-size: 32px;
}

.todo-list {
	list-style-type: none;
}

 
input[type="checkbox"] {
	vertical-align: middle;
  position: relative;
}

 .tick {
	display: inline-block;
  white-space: nowrap;
 } 


</style>


  