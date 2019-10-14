<template>
  <main>
    <div class="suggestion">
      <input type="text" v-model="password" ref="field">
      <button @click="generate" type="button">🔄</button>
    </div>

    <password v-model="password" :strength-meter-only="true"/>
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
  'lighthouse',
  'dog',
  'bone',
  'graveyard',
  'church',
  'plant',
  'tree'
]
let source = new Set(sourceWords)
let generator = new Generator()
generator.analyze(source)

// TODO: Consider using instagrammar instead of wordgenie?
export default {
  name: 'generator',
  data () {
    return {
      password: '',
      separator: '-'
    }
  },
  components: { Password },
  async mounted () {
    await this.$nextTick()
    this.generate()
  },
  methods: {
    generate () {
      const words = generator.genSet(3)
      this.password = Array.from(words).join(this.separator)
      this.$refs.field.focus()
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
  max-width: 25rem;
  border-radius: .25rem;
}
.suggestion {
  margin-bottom: 1.5rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: .5rem;

  button {
    background: none;
    border: none;
    padding: .5rem .75rem;
    border-radius: 4px;
    color: #333;
    font-size: 1rem;
  }
  input {
    display: block;
    background-color: #f1f1f1;
    border: 1px solid #f1f1f1;
    border-radius: 2px;
    box-sizing: border-box;
    font-size: 14px;
    padding: 13px;
    width: calc(100% - 3rem);
  }
}
</style>
