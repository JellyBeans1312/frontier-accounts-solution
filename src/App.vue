<template>
  <div id="app">
    <section class="grid">
      <Accounts v-bind:accounts='accounts'/>
    </section>
  </div>
</template>

<script>
import Accounts from './components/UserAccounts/Accounts'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Accounts
  },
  data() {
    return {
      accounts: []
    }
  },
  created() {
    axios.get('https://frontiercodingtests.azurewebsites.net/api/accounts/getall')
    .then(res => this.accounts = res.data)
    .catch(error => console.log(error))
  }
}

</script>

<style>

</style>
