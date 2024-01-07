<script>
    let user_dict = {
        first_name : 'Ada',
        last_name : 'Lovelace'
    };
</script>

<label>
    <input bind:value={user_dict['first_name']} />
    first_name
</label>

<label>
    <input bind:value={user_dict['last_name']} />
    last_name
</label>

{(console.log(user_dict), '')}

<h1> Hello {user_dict['first_name']}!</h1>https://nownowcdn.com/data/wtimg2/5/4/2054/766865/1703480415_75298270221271.jpg