<template>
  <div>
    <p>Accounts</p>
    <div v-bind:key='account.id' v-for='account in accounts'>
      <AccountContent v-bind:account='account'/>
    </div>
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

</style>