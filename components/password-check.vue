<template>
<div>
  <p>Nouveau mot de passe</p>
  <div>
    <Password v-model="newPassword" />
  </div>
  <div>
    <div>{{hasNumber}}</div>-<div>{{hasUpperCase}}</div>-<div>{{hasLowerCase}}</div>
  </div>
  <p>Confirmation du mot de passe</p>
  <div>
    <Password v-model="confirmPassword" />
  </div>
  <div>
    <div>{{isSame}}</div>
  </div>
</div>
</template>
<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  model: {
    prop: 'newPassword'
  },
  data() {
    return {
      newPassword: '',
      confirmPassword: ''
    }
  },
  computed: {
    hasNumber(): boolean {
      return /[0-9]/.test(this.newPassword);
    },
    hasUpperCase(): boolean {
      return /[A-Z]/.test(this.newPassword);
    },
    hasLowerCase(): boolean {
      return /[a-z]/.test(this.newPassword);
    },
    isSame(): boolean {
      return !!this.newPassword && (this.newPassword === this.confirmPassword);
    },
    isValid(): boolean {
      return this.hasNumber && this.hasUpperCase && this.hasLowerCase && this.isSame;
    }
  },
  watch: {
    isValid(val) {
      this.$emit('input', val ? this.newPassword : '');
    }
  },
})
</script>