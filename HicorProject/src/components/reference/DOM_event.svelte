<script>
    let mouse_position = {x:0, y:0};

    function handleMove(event){
        mouse_position['x'] = event.clientX;
        mouse_position['y'] = event.clientY;
    }
</script>

<div on:pointermove={handleMove}>
    The pointer is ad {mouse_position['x']}  x {mouse_position['y']}
</div>


<style>
    div {
        position : fixed;
        left : 0;
        top : 0;
        width : 100%;
        height : 100%;
        padding : 1rem;
    }
</style>