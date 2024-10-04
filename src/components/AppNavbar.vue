<template>
  <nav>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <div class="text-uppercase nav-item" @click="$router.push('/')">
          Movies
        </div>
      </div>
    </v-app-bar>
  </nav>
</template>

<script>
export default {
  name: 'AppNavbar',
}
</script>

<style scoped>
.nav-item {
  cursor: pointer;
}
</style>
