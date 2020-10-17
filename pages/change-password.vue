<template>
  <div>
    <p>Ancien mot de passe</p>
    <div>
      <Password v-model="oldPassword" />
    </div>
    <PasswordCheck v-model="newPassword" @is-valid="isValid" />
    <button v-if="isValid">Modifier le mot de passe</button>
  </div>
</template>
<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  head: {
    title: 'SOFYA | Changement de mot de passe'
  },
  data() {
    return {
      oldPassword: '',
      newPassword: ''
    };
  },
  computed: {
    isValid(): boolean {
      return !!this.oldPassword && !!this.newPassword;
    }
  },
  watch: {
    oldPassword(val) {
      console.log('OLD', val);
    },
    newPassword(val) {
      console.log('NEW', val);
    }
  }
})
</script>