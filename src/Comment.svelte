<script>
    import moment from 'moment'
    import Like from './like.svg'

    export let comment;

    const getDate = date => {
        return moment(date).fromNow();
    }

</script>

<div class="card" id="card-{comment.id}">
    <div class="card-content">
        <div class="media">
            <div class="media-left">
            <figure class="image is-48x48">
                <img src="{comment.authorProfileImageUrl}" alt="{comment.authorDisplayName}">
            </figure>
            </div>
            <div class="media-content">
                <p class="title is-6">
                    <a href="{comment.authorChannelUrl}" target="_blank">{comment.authorDisplayName}</a>
                    <time datetime="2016-1-1">{getDate(comment.publishedAt)}</time>
                </p>
                <div class="content">
                    {@html comment.textDisplay}
                </div>
                <p class="likes">
                    <Like />
                    <span>{comment.likeCount}</span>
                </p>
            </div>
        </div>
        
    </div>
</div>

<style>
    figure {
        border-radius: 50%;
        overflow: hidden;
    }
    .card {
        box-shadow: none;
        background-color: transparent;
    }
    .card-content {
        padding: 20px 0;
    }
    .title {
        margin-bottom: 5px;
        font-size: 13px;
    }
    .title a {
        font-weight: bold;
        color: #000000;
    }
    .title time {
        color: #606060;
        font-weight: normal;
    }
    .content {
        color: rgb(3, 3, 3);
        font-size: 14px;
    }
    .likes {
        color: #606060;
        font-size: 13px;
        background-position: left center;
        background-size: cover;
    }
    .likes :global(svg) {
        width: 14px;
    }
</style>