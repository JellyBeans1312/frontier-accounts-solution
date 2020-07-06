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
        return {...account, newdate, newPhone}
      })
    )
    .then(res => this.accounts = res)
    .catch(error => console.log(error))
  },
}

</script>

<style>
html, body {
  height: 100%;
  width: 100%;
  font-family: Roboto, Helvetica, Arial, sans-serif
}

article {
  height: 100%;
  grid-template-columns:1fr;
  grid-template-areas:
      "header"
      "main"
      "footer";
  grid-template-rows: 100px 1fr 150px;
}

header {
  grid-area: header;
  background-color:#006643;
  color: #fff;
  grid-template-columns: 1% 98% 1%;
}

h1 {
  font-size: 3em;
  font-weight: bold;
}

h2 {
  font-size: 2em;
  color:#006643;
}

h3 {
  display: block;
  font-size: 1.5em;
  color:#006643;
}

main {
  grid-area: main;
}

footer {
  grid-area: footer;
  background-color:#006643;
  color: #fff;
  grid-template-columns: 1% 98% 1%;
  grid-template-rows: 5% 90% 5%;
}

.grid {
  display: grid;
}

.title-container {
  grid-column-start: 2;
  align-self: center;
}

#home-content {
  grid-row-gap: 25px;
  grid-template-rows: 10px 100px auto;
}

#account-grid {
  grid-template-columns: 1fr 1fr 1fr;
  grid-row-start: 3;
}

.account-column {
  grid-template-rows: 2em repeat(2, 10em);
}

.content-title-container {
  justify-self: center;
  height: 1em;
  grid-row-start: 2;
}
</style>
