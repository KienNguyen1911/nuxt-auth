<template>
  <div>
    <img
      alt="nature"
      class="h-[32rem] w-full object-cover object-center"
      src="https://images.unsplash.com/photo-1485470733090-0aae1788d5af?ixlib=rb-4.0.3&amp;ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&amp;auto=format&amp;fit=crop&amp;w=2717&amp;q=80"
    />
    <h1>OKOK</h1>
  </div>
</template>

<script lang="ts" setup>
definePageMeta({
  middleware: "auth",
  layout: "default",
  title: "Home"
});
const client = useSupabaseClient();
const user = useSupabaseUser();

const signOut = async () => {
  await client.auth.signOut();
  navigateTo("/auth/login");
  console.log("signing out");
};
</script>

<style></style>
