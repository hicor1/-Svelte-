<!------------- JS ------------->
<script>
    let todos = [
        {done: false, text:'finish  Svelte tutorial'},
        {done: false, text:'build an app'},
        {done: false, text:'world domination'},
    ]

    function add() {
        const temp = {done: false, text:'world domination'}
        todos = [...todos, temp]
    }

    function clear() {
        const userconformination = window.confirm('정말로 지우시겠습니까?')
        if (userconformination == true) {
            todos = todos.filter((t) => t['done'] != false)
            alert('삭제 완료')
        } else {
            alert('취소되었습니다.');
        }
    }

    //$: remaining = todos.filter((t) => !t.done).length;
    $: remaining = todos.filter((t) => t['done'] == false).length;


</script>

<!------------- HTML ------------->

<div class="centered">
    <h1>todos</h1>

    <ul class="todos">
        {#each todos as todo}
        <li class:done={todo.done}>
            <input 
                type="checkbox"
                bind:checked={todo.done}
            />

            <input 
                type="text"
                placeholder="What needs to be done"
                bind:value={todo.text}
            />
        </li>
    {/each}
    </ul>

    <p>{remaining} remaining</p>

    <button on:click={add}>
        Add new
    </button>
    <button on:click={clear}>
        Clear completed
    </button>

</div>



<!------------- CSS ------------->
<style>
	.centered {
		max-width: 20em;
		margin: 0 auto;
	}

	.done {
		opacity: 0.4;
	}

	li {
		display: flex;
	}

	input[type="text"] {
		flex: 1;
		padding: 0.5em;
		margin: -0.2em 0;
		border: none;
	}
</style>