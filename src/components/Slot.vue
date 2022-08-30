<template>
  <div class="slot-wrapper">
    <div class="lhs">
      <h2 class="title">Slot</h2>
      <slot v-if="slot[0].slotEnable"></slot>
      <slot name="slot-1" v-if="slot[1].slotEnable"></slot>
      <slot name="slot-2" v-if="slot[2].slotEnable"></slot>
      <slot name="slotCom" v-if="slot[3].slotEnable"></slot>
    </div>
    <div class="rhs">
      <p class="title">Control the slot</p>
      <ul>
        <li v-for="item in slot" v-bind:key="item.key">
          <label :for="item.name"><input type="checkbox" :id="item.name" :checked="item.slotEnable"
              @change="SlotChange(item.key)" />
            {{ item.name }}</label>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Slot",
  props: {
  },
  data() {
    return {
      slotTemplate: '',
      slot: [
        { name: 'default', slotEnable: true, key: 0 },
        { name: 'slot-1', slotEnable: true, key: 1 },
        { name: 'slot-2', slotEnable: true, key: 2 },
        { name: 'slotCom', slotEnable: true, key: 3 }
      ]
    }
  },
  methods: {
    SlotChange(_index) {
      this.slot.forEach((item, index) => {
        if (_index == index)
          item.slotEnable = !item.slotEnable
      })
    }
  }
}
</script>

<style lang="scss">
.slot-wrapper {
  margin-top: 50px;
  font-size: 1.2rem;
  text-align: center;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: flex-start;

  .lhs {
    flex: 2;
  }

  .rhs {
    flex: 1;
  }

  .title {
    font-size: 2.5rem;
    font-weight: bold;
  }

  .default-slot,
  .slot-1,
  .slot-2,
  .SlotCom {
    max-width: 800px;
    margin: 30px auto;
    padding: 50px 100px;
    background-color: aquamarine;
    border-radius: 30px;
  }

  .slot-1 {
    background-color: coral;
  }

  .slot-2 {
    background-color: darkseagreen;
  }

  .SlotCom {
    background-color: lightcoral;
  }
}
</style>