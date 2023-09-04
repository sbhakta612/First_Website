<template>
  <div>Characters:</div>

  <ul>
    <li v-for="character in characterNames" :key="character">{{ character }}</li>
  </ul>
</template>
<script>
export default {
  props: {
    movieObject: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      characterNames: []
    }
  },
  watch: {
    async movieObject() {
      this.characterNames = []

      for (let i = 0; i < this.movieObject.characters.length; i++) {
        const characterURL = this.movieObject.characters[i]

        const response = await fetch(characterURL)
        const result = await response.json()

        this.characterNames.push(result.name)
      }
    }
  }
}
</script>

<style scoped></style>
