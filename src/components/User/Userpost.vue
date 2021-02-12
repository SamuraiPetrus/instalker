<template>
    <div class="column user-post is-one-third">
        <figure class="user-post-image">
            <img :src="post.display_url">
            <div class="user-post-figcaption">
                <a class="content-glass" :href="postUrl" target="_blank"></a>
                <div class="user-post-data is-flex">
                    <div class="mr-5">
                      <i class="fas fa-heart"></i>
                      {{ filteredUserNumber(post.edge_liked_by.count) }}
                    </div>
                    <div class="">
                      <i class="fas fa-comment"></i>
                      {{ filteredUserNumber(post.edge_media_to_comment.count) }}
                    </div>
                </div>
            </div>
        </figure>
    </div>
</template>

<script>
export default {
    props: {
        post: {required: true}
    },
    methods: {
        filteredUserNumber ( num ) {

          return Math.abs(Number(num)) >= 1.0e+9

          ? (Number(num) / 1.0e+9).toFixed(1) + "B"

          : Math.abs(Number(num)) >= 1.0e+6

          ? (Number(num) / 1.0e+6).toFixed(1) + "M"

          : Math.abs(Number(num)) >= 1.0e+4

          ? (Number(num) / 1.0e+3).toFixed(1) + "K"

          : Math.abs(Number(num));
        }
    },
    computed: {
        postUrl: function () {
            return 'https://www.instagram.com/p/' + this.post.shortcode
        }
    }
}
</script>

<style lang="css" scoped>
    .user-post-image,
    .user-post-image img{
        width: 100%;
        height: 300px;
        object-fit: cover;
        position: relative;
    }
    .user-post-figcaption{
        position: absolute;
        top: 0;
        width: 100%;
        height: 100%;
        background: rgba(0,0,0,0.5);
        opacity: 0;
        transition: all .5s;
    }
    .user-post-data{
        color: #fff;
        font-size: 26px;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 100%;
        justify-content: center;
    }
    .content-glass{
        position: absolute;
        width: 100%;
        height: 100%;
        display: flex;
        z-index: 10;
    }
    .user-post-figcaption:hover{
        opacity: 1;
    }
</style>
