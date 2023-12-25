<script setup lang="ts">
const user = useSupabaseUser();
watch(
  user,
  () => {
    if (user.value) {
      return navigateTo("/");
    }
  },
  { immediate: true }
);
</script>
<template>
  <div class="h-screen bg-white">
    <div class="flex justify-center items-center h-full">
      <img
        class="h-16 w-16"
        src="https://icons8.com/preloaders/preloaders/1488/Iphone-spinner-2.gif"
        alt=""
      />
      Waiting for confirmation...
    </div>
  </div>
</template>
