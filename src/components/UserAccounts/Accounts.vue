<template>
  <div>
  <main class="content grid" id="home-content">
  <div class="content-title-container">
    <h2>Accounts</h2>
    <div v-bind:key='account.id' v-for='account in accounts'>
      <AccountContent v-bind:account='account'/>
    </div>
    </div>
    </main>
  </div>
</template>

<script>
import AccountContent from './AccountContent'
export default {
  name: 'Accounts',
  props: ['accounts'],
  components: {
    AccountContent
  }
}
</script>

<style scoped>
  #overdue-account-container-title > h3{
    color: #B22222;
  }
  #inactive-account-container-title > h3 {
    color:#808080;
  }
  .account-container {
    justify-self: center;
    height: 5em;
  }
  .account-container-title {
    justify-self: center;
  }
</style>