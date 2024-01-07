<script>
    // Stores.js 정의
    import { writable } from 'svelte/store';
    
    function createCount() {
        const { subscribe, set, update } = writable(0);

        return {
            subscribe,
            increment:() => update((n) => n+1),
            decrement:() => update((n) => n-1),
            reset: () => set(0)
        };
    }

    export const count  = createCount();

</script>   

<h1> The count is {$count} </h1>

<button on:click={count.increment}>+</button>
<button on:click={count.decrement}>-</button>
<button on:click={count.reset}>reset</button>