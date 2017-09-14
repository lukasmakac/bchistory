<template>
      <form class="deposit" novalidate v-on:submit.prevent>
          <div class="form-group row">
            <label for="amount" class="col-sm-2 col-form-label">Deposit</label>
            <div class="col-sm-10">
              <input class="form-control" @keyup.enter="deposit" type="text" v-model="amount" name="amount"></input>
            </div>
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