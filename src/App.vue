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
    .then(res => res.data.map(account => {
        let date = new Date(account.PaymentDueDate)
        let newdate= (date.getMonth() + 1) + '/' + date.getDate() + '/' +  date.getFullYear();

        // Would refactor and break this into a separate method with more time
        let newPhone;
        let formatPhoneNumber = (str) => {
          let cleaned = ('' + str).replace(/\D/g, '');
          let match = cleaned.match(/^(\d{3})(\d{3})(\d{4})$/);

          if (match) {
            newPhone = '(' + match[1] + ') ' + match[2] + '-' + match[3]
            return newPhone
          }

          return null
          };
          formatPhoneNumber(account.PhoneNumber)
          console.log(newPhone)
        return {...account, newdate, newPhone}
      })
    )
    .then(res => this.accounts = res)
    .catch(error => console.log(error))
  },
}

</script>

<style>

</style>
