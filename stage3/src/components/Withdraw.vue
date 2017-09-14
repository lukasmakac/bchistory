<template>
      <form class="withdraw" novalidate v-on:submit.prevent>
          <div class="deposit-content">
            <label for="amount">Withdraw</label>
            <input  @keyup.enter="withdraw" type="text" v-model="amount" name="amount"></input>
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
    withdraw () {
      this.$emit('withdraw', this.amount)
      this.amount = 0
    }
  }
}
</script>

<style scoped>
</style>