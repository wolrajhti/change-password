<template>
  <input v-model="value" />
</template>
<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  model: {
    prop: 'value'
  },
  data() {
    return {
      value: '',
    }
  },
  watch: {
    value(val) {
      this.$emit('input', val);
    }
  }
})
</script>