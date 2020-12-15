<template>
    <div class="usertag is-flex is-flex-direction-column is-align-items-center pt-5 pb-5">
          <div class="usertag-content is-flex is-align-items-center mb-4">
              <figure class="user-profilepic mr-2">
                  <img src="https://scontent-for1-1.cdninstagram.com/v/t51.2885-19/s150x150/106702189_270769510881748_1608525548909710164_n.jpg?_nc_ht=scontent-for1-1.cdninstagram.com&_nc_ohc=uWoLu28ahOQAX9O0DYs&tp=1&oh=1f4c5403895a262f9aea3b823a6c34a5&oe=60008798" alt="instagram profile picture of Millie Bobby Brown">
              </figure>
              <h3 class="usertag-title is-size-4">@milliebobbybrown</h3>
          </div>
          <Useractions></Useractions>
    </div>
</template>

<script>
import Useractions from './Useractions.vue'
export default {
    components: {
        Useractions
    }
}
</script>

<style lang="css" scoped>
    .usertag{
        width: 100%;
        border-top: 1px solid #c4c4c4;
    }
    .usertag-title{
        width: fit-content;
    }
    .usertag .user-profilepic,
    .usertag .user-profilepic img{
        width: 40px;
        height: 40px;
    }
</style>
