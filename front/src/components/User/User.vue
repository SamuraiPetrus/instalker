<template>
    <div class="user container">
        <div class="pl-4 pr-4">
            <Appheader></Appheader>
            <div class="user-content is-flex is-flex-wrap-wrap is-justify-content-center">
                <Userheader></Userheader>
                <div class="user-posts columns mt-5 mb-5 is-multiline is-full">
                    <Userpost v-for="user in repeatUser(9)" :key="user"></Userpost>
                </div>
                <Usertag></Usertag>
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
        methods: {
            repeatUser( num ) {
                var count = 0,
                    repeat_user_loop = [];
                while ( count < num ) {
                    repeat_user_loop.push(1)
                    count++
                }

                return repeat_user_loop
            }
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
