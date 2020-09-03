<script>
    import { onMount } from 'svelte';
    import Comment from './Comment.svelte'
    import querystring from 'query-string';

    export let videoId;

    let comments = [];
    const endpoint = 'https://www.googleapis.com/youtube/v3/commentThreads';
    const args = {
        videoId,
        part: 'snippet,replies',
        maxResults : 10,
        key : API_KEY
    }

    onMount(async () => {
        let response = await fetch(`${endpoint}?${querystring.stringify(args)}`);
            response = await response.json()
            let { items } = response;
            comments = items;
    });

</script>

<div id="comments">
    {#each comments as { snippet: { topLevelComment: { snippet : comment } } } }
        <Comment {comment} />
    {/each}
</div>