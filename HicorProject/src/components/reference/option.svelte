<script>

    const options = [
        {color:'red', tezt:'RED THING'},
        {color:'green', tezt:'GREEN THING'},
        {color:'blue', tezt:'BLUE THING'},
    ]

    let selected_option = options[0];

</script>


<select bind:value={selected_option['color']}>
    {#each options as option}
        <option value={option['color']}>{option['color']}</option>

    {/each}
</select>