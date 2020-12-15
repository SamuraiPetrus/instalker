<template>
    <div class="searchform is-flex">
        <span class="searchform-error" v-show="errored">{{ errorReason }}</span>
        <div class="control has-icons-left mr-3 is-medium" :class="{ 'is-loading' : loading }">
            <input type="text" v-model="user" placeholder="milliebobbybrown" class="input is-medium is-hovered" :class="{'is-danger' : errored}" @input="onTyping()"/>
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
          loading: false,
          errored: false,
          errorReason: ''
       }
    },
    methods: {
        stalkUser ( user ) {
            if ( user ) {
                this.loading = true
                axios
                .get('https://www.instagram.com/'+ user +'/?__a=1')
                .then( response => {
                    console.log(response.data.graphql)
                    this.found = true
                    Event.fire('stalkUser', response.data.graphql)
                    Event.fire('userFound')
                })
                .catch( error => {
                    this.errored = true
                    switch ( error.response.status ) {
                        case 404 :
                            this.errorReason = "We didn't find this one, try another user!"
                            break
                        default :
                            this.errorReason = "Sorry. We're facing internal server error. :("
                            break
                    }
                })
                .finally(() => {
                    this.loading = false
                })
            } else {
                this.errored = true
                this.errorReason = "Required field. (We can't read minds yet)"
            }
        },
        onTyping() {
            this.errored = false
        }
    }
}
</script>

<style lang="css" scoped>

    .searchform{
        position: relative;
    }
    .searchform-error{
        background: #f14668;
        color: #fff;
        font-size: 13px;
        letter-spacing: 1px;
        position: absolute;
        z-index: 1;
        bottom: -40px;
        padding: 5px 20px;
        border-radius: 5px;
    }
    .searchform-error::before{
        content: "";
        display: block;
        position: absolute;
        top:-3px;
        transform: rotate(45deg);
        background: #f14668;
        z-index: -1;
        height: 20px;
        width: 20px;
    }

</style>
