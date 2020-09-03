<script>
	import Comments from './Comments.svelte';
	import Video from './Video.svelte';
	import Related from './Related.svelte';
	import Header from './Header.svelte';
	import Ricerca from './Ricerca.svelte';
	import 'bulma/css/bulma.css'

	let title ='';
	let videoId = '';
	let idToSearch = '';

</script>

	<Header on:setVideo={e=>idToSearch=e.detail} />

		
		<div class="section section--video">
			<div class="container">
				{#if videoId}
					<div class="columns">
						<div class="column is-two-thirds">
							<Video videoId={videoId} />
							<Comments videoId={videoId} />
						</div>
						<div class="column is-one-third">
							<Related videoId={videoId} />
						</div>
					</div>
				{:else if idToSearch }
					<Ricerca {idToSearch} />
				{/if}
		</div>
	</div>


<style>
	.section--video {
		color: #000;
		background-color: #f9f9f9;
		margin-top: 60px;
	}
</style>