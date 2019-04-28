<template>
  <div>
    <div>account: {{ account }}</div>
    <div>balance: {{ balance }}</div>
  </div>
</template>

<script>
export default {
  computed: {
    account() {
      return this.$store.getters['account'];
    },
    balance() {
      return this.$store.getters['balance'];
    }
  }
};
</script>
