<template>
  <div v-if="movieObject == undefined">Select a Movie on the Left</div>
  <div v-else>
    <h2>Episode {{ movieObject.episode_id }} - {{ movieObject.title }}</h2>
    <p>{{ movieObject.opening_crawl }}</p>
    <div><CharactersList :movieObject="movieObject" /></div>
  </div>
</template>

<script>
import CharactersList from './CharactersList.vue'

export default {
  components: {
    CharactersList
  },
  props: {
    movieObject: {
      type: Object,
      required: false
    }
  }
}
</script>

<style scoped></style>
