<template>
  <div>
      <!-- <b-table hover :items="records"></b-table> -->
      <table>
        <thead>
          <th>Amount</th>
          <th>Type</th>
        </thead>
        <tbody>
          <tr v-for="record in records" :key="record.id">
            <td>{{ record.amount }}</td>
            <td>{{ record.type }}</td>
          </tr>
        </tbody>
      </table>
      <div class="total">
        <span class="label">Total exchanged:  {{ sum }}</span>
      </div>
      <div class="balance">
        <span class="label">Balance:  {{ balance }}</span>
      </div>
      <form class="deposit" novalidate v-on:submit.prevent>
          <div class="deposit-content">
            <label for="amount">Deposit</label>
            <input  @keyup.enter="deposit" type="text" v-model="depositAmount" name="amount"></input>
          </div>
      </form>
      <form class="withdraw" novalidate v-on:submit.prevent>
          <div class="deposit-content">
            <label for="amount">Withdraw</label>
            <input  @keyup.enter="withdraw" type="text" v-model="withdrawAmount" name="amount"></input>
          </div>
      </form>
  </div>
</template>

<script>
import walletData from '../api/wallet.json'
import { TYPES } from '../constants'

export default {
  name: 'wallet',
  data () {
    return Object.assign(walletData, { withdrawAmount: 0, depositAmount: 0 })
  },
  computed: {
    sum () {
      return this.records.map(record => record.amount).reduce((acc, value) => {
        return acc + value
      })
    }
  },

  methods: {
    withdraw () {
      this.records.push({
        amount: Number(this.withdrawAmount),
        date: Date.now(),
        type: TYPES.WITHDRAW
      })

      this.balance -= Number(this.withdrawAmount)
      this.withdrawAmount = 0
    },
    deposit () {
      this.records.push({
        amount: Number(this.depositAmount),
        date: Date.now(),
        type: TYPES.DEPOSIT
      })
      this.balance += Number(this.depositAmount)
      this.depositAmount = 0
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  table {
    border-collapse: collapse
  }
  table, th, td{
    border: 1px solid
  }

  .total, .balance{
    text-align: left;
    font-weight: bold
  }
</style>
