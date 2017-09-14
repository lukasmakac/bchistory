<template>
      <form class="withdraw" novalidate v-on:submit.prevent>
          <div class="form-group row">
            <label for="amount" class="col-sm-2 col-form-label">Withdraw</label>
            <div class="col-sm-10">
              <input class="form-control"  @keyup.enter="withdraw" type="text" v-model="amount" name="amount"></input>
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
    withdraw () {
      this.$emit('withdraw', this.amount)
      this.amount = 0
    }
  }
}
</script>

<style scoped>
  .withdraw-content {
    display: flex;
    align-items: flex-start;
    padding: 10px;
  }
</style>