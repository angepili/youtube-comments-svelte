<script>
    export let comment;

    const getDate = date => {
        const newDate = new Date(date);
        return `${newDate.getHours()}:${newDate.getMinutes()} - ${newDate.getDate()}/${newDate.getMonth()}/${newDate.getFullYear()}`
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
            <p class="title is-6"><a href="{comment.authorChannelUrl}" target="_blank">{comment.authorDisplayName}</a></p>
            </div>
        </div>
        <div class="content">
            {@html comment.textDisplay}
        </div>
        <div class="tags has-addons">
            <time class="tag  is-primary is-light" datetime="2016-1-1">{getDate(comment.publishedAt)}</time>
            <span class="tag"><img src="{comment.likeIcon}" class="likeIcon" alt="" />{comment.likeCount}</span>
        </div>
    </div>
</div>

<style>
    .card {
        margin-bottom: 30px;
    }
</style>