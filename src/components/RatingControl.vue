<template>
  <ul>
    <li :class="{active: activeOption === 'poor'}"><button type="button" @click="activate('poor')">poor</button></li>
    <li :class="{active: activeOption === 'average'}"><button type="button" @click="activate('average')">average</button></li>
    <li :class="{active: activeOption === 'good'}"><button type="button" @click="activate('good')">good</button></li>
  </ul>
</template>

<script>
export default {
  props: ['modelValue'], // when v-model is used on custom comp, child comp will be listening to 'modelValue' and emit 'update:modelValue'
  emits: ['update:modelValue'],
  // data() {
  //   return {
  //     activeOption: this.modelValue
  //   };
  // },
  computed: {
    activeOption() {
      return this.modelValue;
    }
  },
  methods: {
    activate(value) {
      this.activeOption = value;
      this.$emit('update:modelValue', value);
    }
  }
}
</script>

<style scoped>
  .active {
    border-color: purple;
  }

  .active button {
    color: purple;
  }

  ul {
    list-style: none;
    margin: 0.5rem 0;
    padding: 0;
    display: flex;
  }

  li {
    margin: 0 1rem;
    border: 1px solid #ccc;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  button {
    font: inherit;
    border: none;
    background-color: transparent;
    cursor: pointer;
  }
</style>