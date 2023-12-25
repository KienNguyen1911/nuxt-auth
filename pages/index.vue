<template>
  <div>
    <h1>Hello index</h1>
    <button @click="signOut">Sign out</button>
  </div>
</template>

<script lang="ts" setup>
definePageMeta({
  middleware: 'auth'
})
const client = useSupabaseClient()
const user = useSupabaseUser()

const signOut = async () => {
  await client.auth.signOut()
  navigateTo('/auth/login')
  console.log('signing out')
}

</script>

<style>

</style>