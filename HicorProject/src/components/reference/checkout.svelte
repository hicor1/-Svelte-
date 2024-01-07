<script>
    let Ischecked = false;
    import Alert from './alert.svelte'
</script>

<label>
    <input type='checkbox' bind:checked={Ischecked}/>
    Yes! Send me regular email spam
</label>

{#if Ischecked == true}
    <p>
		Thank you. We will bombard your inbox and sell
		your personal details.
    </p>

{:else}
    <p>
        You must opt in to continue. If you're not
        paying, you're the product.
    </p>
{/if}

<button disabled={!Ischecked} on:click={()=>alert('가즈아')}>Subscribe</button>