<template>
    <div class="user-actions">
        <button class="button is-success mr-3" type="button" name="button"><i class="fas fa-eye mr-2"></i> Stalk</button>
        <a :href="fullProfileUrl" class="button is-info is-instagram" target="_blank"><i class="fab fa-instagram mr-2"></i> View full profile</a>
    </div>
</template>

<script>
export default {
  props: {
    user: { required: true }
  },
  computed: {
      fullProfileUrl: function () {
          return 'https://www.instagram.com/' + this.user.username
      }
  },
}
</script>

<style lang="css" scoped>
</style>
