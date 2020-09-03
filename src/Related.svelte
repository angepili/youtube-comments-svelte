<script>
    import { onMount } from 'svelte'
    import querystring from 'query-string';
    import moment from 'moment'

    export let videoId;

    let items = [];

    const endpoint = 'https://www.googleapis.com/youtube/v3/search',
					args = {
					    relatedToVideoId: videoId,
					    part: 'snippet',
					    type: 'video',
					    key : API_KEY,
					    maxResults: 10
					}
								
    onMount(async () => {
        let response = await fetch(`${endpoint}?${querystring.stringify(args)}`);
            response = await response.json()
            items = response.items;
    });

</script>

<div id="related">
    {#each items as { publishedAt, snippet: { title, publishedAt, description, channelTitle, thumbnails: { medium: { url: imageurl }} }} }
        <div class="related">
            <div class="columns is-multiline is-mobile">
                <div class="column is-half">
                    <img src={imageurl} alt="{title}" class="thumbnail" />
                </div>
                <div class="column is-half">
                    <h2>{title}</h2>
                    <p>{  moment(publishedAt).fromNow() }</p>
                </div>
            </div>
        </div>
    {/each}
</div>

<style>
    .thumbnail {
        max-width: 100%;
        height: auto;
    }
    h2 {
        font-size: 14px;
        font-weight: bold;
        margin-bottom: 10px;
    }
    p {
        color: #606060;
        font-weight: 400;
        font-size: 13px;
    }
</style>