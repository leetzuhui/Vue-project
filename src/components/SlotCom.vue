<template>
  <div :class="name">
    This is the {{ name }} section from <b>SlotCom.vue</b>. <br />
    <code>v-slot: {{ name }}</code> in the Base component is indicated to show it's a named slot. <br />
    <code>name="{{ name }}"</code> in the Derived component means that only named slot defined in Base component can be
    replaced here.
  </div>
</template>

<script>
export default {
  name: 'SlotCom',
  props: {

  },
  data() {
    return {
      name: 'SlotCom'
    }
  },
  methods: {
  }
}
</script>

<style>
</style>