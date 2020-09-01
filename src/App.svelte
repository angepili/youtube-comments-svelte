<script>
	import Comments from './Comments.svelte';
	import 'bulma/css/bulma.css'
</script>

<svelte:head>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" />
</svelte:head>

<div class="container">
	<div class="columns" style="background:red">
		<div class="column is-two-thirds">
			<Comments videoId={'9EcjWd-O4jI'} />
		</div>
		<div class="columns is-one-third"></div>
	</div>
</div>