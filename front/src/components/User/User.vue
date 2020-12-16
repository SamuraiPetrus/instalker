<template>
    <div class="user container" v-show="found">
        <div class="pl-4 pr-4">
            <Appheader></Appheader>
            <div class="user-content is-flex is-flex-wrap-wrap is-justify-content-center">
                <Userheader :user="user">
                </Userheader>
                <div class="user-posts columns mt-5 mb-5 is-multiline is-full">
                    <Userpost v-for="post in media" :key="post.node.id" :post="post.node" ></Userpost>
                </div>
                <Usertag :user="user"></Usertag>
            </div>
            <Appfooter></Appfooter>
        </div>
    </div>
</template>

<script>

    import Appheader from '../Appheader.vue'
    import Userheader from './Userheader.vue'
    import Userpost from './Userpost.vue'
    import Usertag from './Usertag.vue'
    import Appfooter from '../Appfooter.vue'

    export default {
        components: {
            Appheader,
            Userheader,
            Userpost,
            Usertag,
            Appfooter
        },

        data() {
            return {
                found: false,
                user: {},
                media: []
            }
        },

        methods: {
            repeatUser( num ) {
                var count = 0,
                    repeat_user_loop = [];
                while ( count < num ) {
                    repeat_user_loop.push(1)
                    count++
                }

                return repeat_user_loop
            },

            getStalkedUser ( user ) {
                this.found = true;
                this.user = {
                    username:  user.username,
                    posts: user.edge_owner_to_timeline_media.count,
                    followed:  user.edge_followed_by.count,
                    follow:  user.edge_follow.count,
                    full_name: user.full_name,
                    profile_pic: user.profile_pic_url_hd,
                    biography: user.biography,
                    external_url:  user.external_url,
                    is_verified: user.is_verified
                };

                this.media = user.edge_owner_to_timeline_media.edges
            }
        },

        created () {
            Event.listen('stalkUser', ( user ) => { this.getStalkedUser( user ) })
            Event.listen('backToHome', () => this.found = false)
        }
    }

</script>

<style>
    .user-posts,
    .user-more{
        width: 100%;
    }
    .user-profilepic img{
        height: 200px;
        width: 200px;
        border-radius: 200px;
    }
</style>
