<template>
  <div class="pe-wrapper">
    <h2>Props and Emit</h2>
    <h3 class="sub-title props">Props</h3>
    <p>String: {{ PES }}</p>
    <p>String: {{ PED }}</p>
    <p>Number: {{ PEN }}</p>
    <p>Object: {{ PEO }}</p>
    <p>Object: {{ iPhone }}</p>
    <h3 class="sub-title emit">Emit</h3>
    <button @click="ClickMe">Click Me to Invoke the method defined in the <b>PropsAndEmit.vue</b></button>
    <br />
    <p>Current Apperance Mode: {{ ApperanceMode ? 'Light' : 'Dark' }}</p>
    <button @click="ToggleApperanceMode">Toogle Light / Dark Mode</button>
  </div>
</template>

<script>
export default {
  name: 'PropsAndEmit',
  props: {
    PES: String,
    PED: String,
    PEN: Number,
    PEO: Object,
    ApperanceMode: Boolean
  },
  data() {
    return {
      iPhone: { name: 'iPhone 14', model: 'A3642', stroage: 256, price: 899 }
    }
  },
  methods: {
    ClickMe() {
      this.$emit('NameFromDerived', this.iPhone)
    },
    ToggleApperanceMode() {
      this.$emit('ApperanceMode')
    }
  }
}
</script>

<style lang="scss">
.pe-wrapper {
  h2 {
    font-size: 2.5rem;
    font-weight: bold;
  }
}
</style>