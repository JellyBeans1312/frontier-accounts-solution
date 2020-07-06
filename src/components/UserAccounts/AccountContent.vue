<template>
  <div class="account-container">
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
  .account-data-list {
    list-style: none;
  }
  .account-data-list > li {
    margin: 10px 0;
  }
  .account-data-list > li > label {
    font-weight: bold;
    margin: 0 5px 0 0;
  }

</style>