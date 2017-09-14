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
        <p> {{ sum }} </p>
      </div>
  </div>
</template>

<script>
import walletData from '../api/wallet.json'

export default {
  name: 'wallet',
  data () {
    return walletData
  },
  computed: {
    sum () {
      return
    }
  },

  methods: {
    withdraw () {
    },
    deposit () {
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
</style>
