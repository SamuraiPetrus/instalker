<template>
    <div class="userheader is-flex is-justify-content-center mb-5 mt-5 is-flex-wrap-wrap">
        <figure class="user-profilepic mr-6">
            <img :src="user.profile_pic" alt="instagram profile picture of Millie Bobby Brown">
        </figure>
        <div class="user-header">
            <div class="is-flex is-align-items-center">
                <h1 class="is-size-3 mb-3">{{ user.username }}</h1>
                <svg v-if="user.is_verified" class="ml-3" width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect width="20" height="20" rx="10" fill="#2B95E9"/>
                <path fill-rule="evenodd" clip-rule="evenodd" d="M12.8847 7.21735C13.0247 7.07862 13.2136 7.00055 13.4106 7C13.6077 6.99946 13.797 7.07649 13.9378 7.21445C14.0785 7.3524 14.1592 7.54019 14.1626 7.73722C14.166 7.93425 14.0916 8.12468 13.9557 8.26735L9.96371 13.2574C9.8951 13.3312 9.81229 13.3906 9.72024 13.4317C9.62819 13.4729 9.52878 13.4951 9.42796 13.4969C9.32714 13.4988 9.22698 13.4803 9.13347 13.4426C9.03995 13.4049 8.95501 13.3487 8.88371 13.2774L6.23871 10.6314C6.16502 10.5627 6.10592 10.4799 6.06493 10.3879C6.02394 10.2959 6.00189 10.1966 6.00012 10.0959C5.99834 9.99517 6.01686 9.89514 6.05459 9.80175C6.09231 9.70836 6.14845 9.62353 6.21967 9.55231C6.29089 9.48109 6.37572 9.42495 6.46911 9.38723C6.5625 9.34951 6.66253 9.33098 6.76323 9.33276C6.86393 9.33454 6.96325 9.35658 7.05525 9.39757C7.14725 9.43856 7.23005 9.49766 7.29871 9.57135L9.39271 11.6644L12.8657 7.23935C12.8719 7.2316 12.8786 7.22426 12.8857 7.21735H12.8847Z" fill="white"/>
                </svg>
            </div>
            <ul class="user-numbers is-flex mb-5">
                <li class="user-number mr-5">
                    <strong>{{ filteredUserNumber(user.posts) }}</strong>
                    posts
                </li>
                <li class="user-number mr-5">
                    <strong>{{ filteredUserNumber( user.followed ) }}</strong>
                    followers
                </li>
                <li class="user-number mr-5">
                    <strong>{{ filteredUserNumber(user.follow) }}</strong>
                    following
                </li>
            </ul>
            <div v-if="user.full_name || user.biography || user.external_url" class="user-bio mb-5">
                <h2 v-if="user.full_name"><strong>{{ user.full_name }}</strong></h2>
                <p v-if="user.biography" class="mt-3">{{ user.biography }}</p>
                <a v-if="user.external_url" class="mt-3 is-inline-block" target="_blank" :href="user.external_url">{{ user.external_url }}</a>
            </div>
            <Useractions :user="user"></Useractions>
        </div>
    </div>
</template>

<script>
    import Useractions from './Useractions.vue';
    export default {
        components: {
            Useractions
        },

        props: {
            user: {required: true}
        },

        methods: {
            filteredUserNumber ( num ) {
                // Nine Zeroes for +1B
                return Math.abs(Number(num)) >= 1.0e+9

                ? (Number(num) / 1.0e+9).toFixed(1) + "B"
                // Six Zeroes for for +1M
                : Math.abs(Number(num)) >= 1.0e+6

                ? (Number(num) / 1.0e+6).toFixed(1) + "M"

                // Five Zeroes for +10K
                : Math.abs(Number(num)) >= 1.0e+4

                ? (Number(num) / 1.0e+3).toFixed(1) + "K"

                : Math.abs(Number(num));
            }
        },
    }
</script>

<style>
    .user-header{
        max-width: 430px;
    }
    @media screen and ( max-width: 700px ) {
        .userheader{
            flex-direction: column;
            justify-content: center !important;
        }
        .user-profilepic{
            width: 200px;
            align-self: center;
            margin-right: 0 !important;
        }
    }
</style>
