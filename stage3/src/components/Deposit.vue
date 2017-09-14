<template>
      <form class="deposit" novalidate v-on:submit.prevent>
          <div class="deposit-content">
            <label for="amount">Deposit</label>
            <input  @keyup.enter="deposit" type="text" v-model="amount" name="amount"></input>
          </div>
      </form>
</template>

<script>
export default {
  data () {
    return {
      amount: 0
    }
  },

  methods: {
    deposit () {
      this.$emit('deposit', this.amount)
      this.amount = 0
    }
  }
}
</script>

<style scoped>
</style>