<template>
  <div>
      <!-- <b-table hover :items="records"></b-table> -->
      <deposit v-on:deposit="deposit"></deposit>
      <withdraw v-on:withdraw="withdraw"></withdraw>
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
  </div>
</template>

<script>
import walletData from '../api/wallet.json'
import { TYPES } from '../constants'
import Withdraw from './Withdraw'
import Deposit from './Deposit'

export default {
  name: 'wallet',
  data () {
    return walletData
  },

  computed: {
    sum () {
      return this.records.map(record => record.amount).reduce((acc, value) => {
        return acc + value
      })
    }
  },

  components: {
    'withdraw': Withdraw,
    'deposit': Deposit
  },

  methods: {
    withdraw (amount) {
      this.records.push({
        amount: Number(amount),
        date: Date.now(),
        type: TYPES.WITHDRAW
      })

      this.balance -= Number(amount)
    },
    deposit (amount) {
      this.records.push({
        amount: Number(amount),
        date: Date.now(),
        type: TYPES.DEPOSIT
      })
      this.balance += Number(amount)
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
