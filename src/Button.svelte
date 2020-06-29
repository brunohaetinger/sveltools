<script>
	export let value;
</script>

<main>
	<button on:click>{value}</button>
</main>

<style>
	button{
        border: 1px gray solid;
        height: 40px;
        width: 40px;
        border-radius: 25%;
        font-weight: bolder;
        margin: 5px;
    }
</style>