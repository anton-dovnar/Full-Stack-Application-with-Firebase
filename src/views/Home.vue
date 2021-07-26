<template>
  <div class="mt-3">
    <div class="text-secondary text-center">
      <div v-if="user" class="text-center">
        Welcome back
        <span class="fw-bold text-info">{{ user }}</span>,
        <a href="#" role="button" class="text-primary" @click="$emit('logout')">logout</a>
      </div>
    </div>
    <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Repellendus, excepturi laudantium porro assumenda dolorem laborum asperiores quos sequi corrupti, tempore accusantium debitis explicabo. Totam officia expedita, minima provident iusto nisi?</p>
  </div>
</template>

<script>
export default {
  name: 'home',
  props: ['user']
}
</script>
