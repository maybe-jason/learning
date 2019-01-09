<template>
  <div>
    <h1 v-if='name === "Jessica"'>My name is Jessica!</h1>
    <h1 v-else>My name is Jason!</h1>
  </div>
</template>

<script>
import OtherComponent from './OtherComponent.vue'

export default {
  name: 'PogComponent',
  components: {
    OtherComponent
  },
  props: ['prop1', 'prop2'],
  data: function () {
    dog: 'Oreo',
    pog: true
  },
  methods: {
    foo: function () { }
    bar: function () { }
  }
}
</script>

<style lang="css" scoped>
</style>
