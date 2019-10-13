<template>
  <main>
    <password v-model="password"
      :toggle="true"/>
  </main>
</template>

<script>
import Password from 'vue-password-strength-meter'
import Generator from 'wordgenie'

const sourceWords = [
  'monday',
  'tuesday',
  'wednesday',
  'wedding',
  'dingo',
  'demon',
  'daylight',
  'sunlight',
  'lighthouse'
]
let source = new Set(sourceWords)
let generator = new Generator()
generator.analyze(source)

export default {
  data: () => ({
    password: this.generate()
  }),
  components: { Password },
  methods: {
    generate () {
      this.password = generator.genWord()
    }
  }
}
</script>

<style lang="scss">
main {
  font-family: 'SFMono-Regular', Menlo, Consolas, 'Liberation Mono', Courier, monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #223;
  margin: 3rem auto;
  width: 94%;
  max-width: 45rem;
  padding: 5rem;
  background-color: cornflowerblue;
  border-radius: .25rem;
}
</style>
