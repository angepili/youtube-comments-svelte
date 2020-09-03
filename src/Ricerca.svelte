<script>
    import { onMount } from 'svelte';
    import Comment from './Comment.svelte'
    import querystring from 'query-string';
    import moment from 'moment'
    import {
        createEventDispatcher
    } from 'svelte';

    
    export let idToSearch;
    
    const dispatch = createEventDispatcher();
    let results = [];
    const endpoint = 'https://www.googleapis.com/youtube/v3/search';
    const args = {
        part: 'snippet',
        maxResults : 10,
        key : API_KEY,
        q : idToSearch,
        type: 'video'
    }

    onMount(async () => {
        let response = await fetch(`${endpoint}?${querystring.stringify(args)}`);
            response = await response.json()
            let { items } = response;
            results = items;
    });

    const getDate = date => {
        return moment(date).fromNow();
    }
</script>

<section>
    <div class="container">
        {#each results as item }
            <div class="card" id="card-{item.id.videoId}" on:click={()=>dispatch('setVideo',item.id.videoId)}>
                <div class="card-content">
                    <div class="media">
                        <div class="media-left">
                        <figure class="image is-128-x128">
                            <img src="{item.snippet.thumbnails.medium.url}" alt="{item.snippet.title}">
                        </figure>
                        </div>
                        <div class="media-content">
                            <p class="title is-6">
                                <span>{item.snippet.title}</span>
                                <time datetime="2016-1-1">{getDate(item.snippet.publishedAt)}</time>
                            </p>
                            <div class="content">
                                {@html item.snippet.description}
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        {/each}
    </div>
</section>

<style>
    section {
        margin: 30px 0;
    }
    .title span {
        font-size: 16px;
    }
    .title time {
        color: #606060;
        font-size: 13px;
    }
    .card {
        cursor: pointer;
        -webkit-transition: all .25s ease-in-out;
        -moz-transition: all .25s ease-in-out;
        -o-transition: all .25s ease-in-out;
        transition: all .25s ease-in-out;
    }
    .card:hover {
        background: #f9f9f9;
    }
</style>