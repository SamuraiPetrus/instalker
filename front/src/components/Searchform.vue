<template>
    <div class="is-flex">
        <div class="control has-icons-left mr-3 is-medium" :class="{ 'is-loading' : loading }">
            <input type="text" v-model="user" placeholder="milliebobbybrown" class="input is-medium is-hovered"/>
            <span class="icon is-left">
                <i class="fas fa-at"></i>
            </span>
        </div>
        <button class="button is-hovered is-medium" type="button" name="button" @click="stalkUser( user )"><i class="fas fa-search"></i></button>
    </div>
</template>

<script>
const axios = window.axios
export default {
    data() {
       return {
          user: "",
          loading: false
       }
    },
    methods: {
        stalkUser ( user ) {
            this.loading = true
            axios
            .get('https://www.instagram.com/'+ user +'/?__a=1')
            .then( response => {
                console.log(response.data)
            })
            .catch( error => {
                console.log( error )
            })
            .finally(() => {
                this.loading = false
            })
        }
    }
}
</script>

<style lang="css" scoped>
</style>
