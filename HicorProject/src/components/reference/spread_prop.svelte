<script>
    export let name = "temp";
    export let version = 0;
    export let speed = "temp";
    export let website = "temp";

    $: href = `https://www.npmjs.com/package/${name}`;
</script>

<p>
	The <code>{name}</code> package is {speed} fast. Download version {version} from
	<a {href}>npm</a> and <a href={website}>learn more here</a>
</p>

