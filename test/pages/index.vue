<template lang="pug">
  div(class="app__container")
    Navigator
    Posts
</template>

<script>
import Vue from 'vue'
import Navigator from '@/components/Navigator.vue'
import Posts from '@/components/Posts.vue'

export default Vue.extend({
  name: 'IndexPage',
  components: {
    Navigator,
    Posts
  }
})
</script>


<style lang="sass" scoped>
</style>