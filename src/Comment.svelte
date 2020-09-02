<script>
    import moment from 'moment'
    export let comment;

    const getDate = date => {
        return moment(date).format('HH:mm DD/MM/YYYY');
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
                    <svg viewBox="0 0 24 24" preserveAspectRatio="xMidYMid meet">
                        <g class="style-scope yt-icon">
                            <path d="M1 21h4V9H1v12zm22-11c0-1.1-.9-2-2-2h-6.31l.95-4.57.03-.32c0-.41-.17-.79-.44-1.06L14.17 1 7.59 7.59C7.22 7.95 7 8.45 7 9v10c0 1.1.9 2 2 2h9c.83 0 1.54-.5 1.84-1.22l3.02-7.05c.09-.23.14-.47.14-.73v-1.91l-.01-.01L23 10z" class="style-scope yt-icon"></path>
                        </g>
                    </svg>
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
        padding-left: 20px;
        background-position: left center;
        background-size: cover;
    }
    .likes svg {
        width: 14px;
    }
</style>