<script>
    // 변수 선언
    let count = 0;
    // 기능정의
    function increment() {
        count += 1;
    }

</script>


<!-- HTML 영역 -->
<button on:click={increment}>
    Clicked {count}
    {count == 1 ? 'time' : 'times'}
</button>

{#if count > 10}
    <p>{count} is greater than 10</p>
{:else if count < 5}
    <p>{count} is less than 5</p>
{:else}
    <p>{count} is between 5 and 10</p>
{/if}