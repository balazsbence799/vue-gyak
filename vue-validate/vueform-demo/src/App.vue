<template>
  <div id="app">
    <h1>VueForm Builder Demo</h1>
    <CreateAccount />
  </div>
</template>

<script>
import CreateAccount from './components/CreateAccount.vue'

export default {
  name: 'App',
  components: { CreateAccount }
}
</script>

<style>
h1 {
  text-align: center;
  color: #1f2937;
  margin-bottom: 2rem;
  font-size: 2rem;
}
</style>