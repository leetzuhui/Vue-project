<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <h1 class="title">Created by TZUHUI</h1>
  <HelloWorld msg="Welcome to Your Vue.js App" />
  <Slot>
    <div class="default-slot">
      This is the default slot section. <br />
      No extra slot name needed.
    </div>
    <template v-slot:slot-1>
      <div class="slot-1">
        This is the slot-1 section. <br />
        <code>v-slot: slot-1</code> in the Base component is indicated to show it's a named slot. <br />
        <code>name="slot-1"</code> in the Derived component means that only named slot defined in Base component can be
        replaced here.
      </div>
    </template>
    <template v-slot:slot-2>
      <div class="slot-2">
        This is the slot-2 section. <br />
        <code>v-slot: slot-2</code> in the Base component is indicated to show it's a named slot. <br />
        <code>name="slot-2"</code> in the Derived component means that only named slot defined in Base component can be
        replaced here.
      </div>
    </template>
    <template v-slot:slotCom>
      <SlotCom />
    </template>
  </Slot>
  <PropsAndEmit PES="Static Props" :PED="PED" :PEN="PEN" :PEO="PEO" @NameFromDerived="InvokedInBased"
    @ApperanceMode="ToggleApperanceMode" :ApperanceMode="ApperanceMode" />
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import Slot from './components/Slot'
import SlotCom from './components/SlotCom'
import PropsAndEmit from './components/PropsAndEmit.vue'

export default {
  name: "App",
  components: {
    HelloWorld,
    Slot,
    SlotCom,
    PropsAndEmit
  },
  data() {
    return {
      ApperanceMode: true,// true for light, false for dark
      PED: 'Dynamic Props',
      PEN: 1984,
      PEO: {
        name: 'Tzu-Hui Lee',
        age: 25,
        job: 'Developer'
      }
    }
  },
  methods: {
    InvokedInBased(e) {
      alert('Name: ' + e.name + '\nModel: ' + e.model + '\nStroage: ' + e.stroage + 'GB\nPrice: $' + e.price)
    },
    ToggleApperanceMode() {
      document.body.classList.toggle('dark')
      if (this.ApperanceMode)
        // light
        this.ApperanceMode = false
      else
        // dark
        this.ApperanceMode = true
    }
  },
};
</script>

<style lang="scss">
#app {
  text-align: center;
  margin-top: 60px;
}
</style>
