<template>
  <div>
    <ul class="account-data-list">
      <li><label>Name: </label>{{account.LastName}}, {{account.FirstName}}</li>
      <li><label>Email: </label>{{account.Email}}</li>
      <li><label>Phone Number: </label>{{account.newPhone}}</li>
      <li><label>Amount Due: </label>${{account.AmountDue}}</li>
      <li><label>Due Date: </label>{{account.newdate}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'AccountContent',
  props: ['account']
}
</script>

<style scoped>

</style>