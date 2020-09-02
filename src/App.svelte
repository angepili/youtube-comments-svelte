<script>
	import Comments from './Comments.svelte';
	import Video from './Video.svelte';
	import Related from './Related.svelte';
	import Header from './Header.svelte';
	import 'bulma/css/bulma.css'
</script>

	<Header />

	<div class="section section--video">
		<div class="columns">
			<!-- <div class="column is-two-thirds">
				<Video videoId={'9EcjWd-O4jI'} />
				<Comments videoId={'9EcjWd-O4jI'} />
			</div>
			<div class="column is-one-third">
				<Related videoId={'9EcjWd-O4jI'} />
			</div> -->
		</div>
	</div>


<style>
	.section--video {
		color: #000;
		background-color: #f9f9f9;
	}
</style>