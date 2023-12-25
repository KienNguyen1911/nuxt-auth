<script setup lang="ts">
const supabase = useSupabaseClient();
const email = ref("");

const signInWithOtp = async () => {
  const { error } = await supabase.auth.signInWithOtp({
    email: email.value,
    options: {
      emailRedirectTo: "http://localhost:3000/auth/confirm"
    }
  });
  if (error) console.log(error);
};

const signInWithOAuth = async () => {
  const { error } = await supabase.auth.signInWithOAuth({
    provider: 'github',
    options: {
      redirectTo: 'http://localhost:3000/auth/confirm',
    },
  })
  if (error) console.log(error)
}
</script>
<template>
  <div>
    <button @click="signInWithOtp">Sign In with E-Mail</button>
    <input v-model="email" type="email" />
    <button @click="signInWithOAuth">Sign In with GitHub</button>
  </div>
</template>
