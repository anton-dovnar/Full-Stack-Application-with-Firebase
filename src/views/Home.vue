<template>
  <div class="mt-3">
    <div class="text-secondary text-center">Welcome back <span class="fw-bold text-info">{{ user }}</span></div>
    <h1>Welcome</h1>
  </div>
</template>

<script>
export default {
  name: 'home',
  props: ['user']
}
</script>
