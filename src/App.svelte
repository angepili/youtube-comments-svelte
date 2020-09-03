<script>
	import Comments from './Comments.svelte';
	import Video from './Video.svelte';
	import Related from './Related.svelte';
	import Header from './Header.svelte';
	import Ricerca from './Ricerca.svelte';
	import Home from './Home.svelte'
	import 'bulma/css/bulma.css'

	let title = '';
	let videoId = '';
	let idToSearch = '';
</script>

<section>
	
	{#if (videoId || idToSearch)}
		<Header on:setVideo={e=>idToSearch=e.detail} />
		{#if videoId}
			<section class="video-main">
				<div class="container">
					<div class="columns">
						<div class="column is-two-thirds">
							<Video videoId={videoId} />
							<Comments videoId={videoId} />
						</div>
						<div class="column is-one-third">
							<Related videoId={videoId} />
						</div>
					</div>
				</div>
			</section>
		{:else if idToSearch }
			<Ricerca {idToSearch} on:setVideo={e=>videoId=e.detail} />
		{/if}
	{:else}
		<Home on:setVideo={e=>idToSearch=e.detail}/>
	{/if}

</section>

<style>
	.video-main {
		margin: 30px 0;
	}
</style>