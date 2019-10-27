<script>
    import TodoItem from './TodoItem.svelte'

    let newTodoTitle = '';
    let currentFilter = 'all';
    let nextId = 4;
    let todos = [
        { id: 1, title: 'First Todo', completed: false },
        { id: 2, title: 'Second Todo', completed: false },
        { id: 3, title: 'Third Todo', completed: false }
    ]
</script>

<div class="container">
    <img src={'/img/logo_id.png'} alt="IvanDjoh's Logo">

    <h3>TodoSvelte</h3>
    <input type="text" class="todo-input" placeholder="Insert Todo Item..." bind:value={newTodoTitle} on:keydown={addTodo}>

    {#each filteredTodos as todo}
        <div class="todo-item">
            <TodoItem {...todo} on:deleteTodo={handleDeleteTodo} on:toggleComplete={handleToggleComplete} />
        </div>
    {/each}

    <div class="inner-container">
        <div>
            <label>
                <input class="inner-container-input" type="checkbox" on:change={checkAllTodos}>Check All
            </label>
        </div>
        <div>{todosRemaining}</div>
    </div>
</div>