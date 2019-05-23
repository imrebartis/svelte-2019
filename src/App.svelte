<script>
	let name = 'Mix';
	let page = 1;
	
	function incrementPage() {
		page += 1
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {name}, my page is {page}!</h1>
<button on:click="{incrementPage}">Change page</button>
