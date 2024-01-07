<script>

    let things = [
        {id : 1, name : 'apple',    symbols : '🍎'},
        {id : 2, name : 'banana',   symbols : '🍌'},
        {id : 3, name : 'carrot',   symbols : '🥕'},
        {id : 4, name : 'doughnut', symbols : '🍩'},
        {id : 5, name : 'egg',      symbols : '🥚'},
    ]

    function handleClick() {
        things = things.slice(1); // list에서 첫번째 행 삭제
    }
</script>

<button on:click = {handleClick}>
    Remove first thing
</button>

{#each things as thing}
    <p>{thing['symbols']} = {thing['name']}</p>
{/each}    