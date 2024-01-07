<script>
    function popAlert(msg) {
      alert(msg);
    }
</script>

<button on:click={()=> popAlert("clicked!!")}>
    Click me
</button>