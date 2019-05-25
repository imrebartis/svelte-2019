<script>
	let name = 'Mix';
	let page = 1;

	$: uppercaseName = name.toUpperCase();
	
	function incrementPage() {
		page += 1
	}

	function changeName() {
		name = 'Fix';
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {uppercaseName}, my page is {page}!</h1>
<button on:click='{incrementPage}'>Change page</button>
<button on:click='{changeName}'>Change name</button>
