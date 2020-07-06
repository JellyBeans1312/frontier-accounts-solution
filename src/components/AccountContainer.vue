<template>
  <section class="grid" id="account-grid">
    <section class="account-column grid" id="active-account-column">
      <div class="account-container-title" id="active-account-container-title">
        <h3>Active</h3>
      </div>
      <AccountContent v-bind:account='account' />
    </section>
  </section>
</template>

<script>
import AccountContent from './UserAccounts/AccountContent'
export default {
  name: 'AccountContainer',
  props: ['account'],
  components: {
    AccountContent
  }
}
</script>