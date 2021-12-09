<template>
  <div class="layout-root">
    <Navbar />
    <slot />
    <Footer />
  </div>
</template>

<script lang="ts">
import Navbar from '~~/components/WizmiNavbar.vue'
import Footer from '~~/components/WizmiFooter.vue'

export default {
  components: { Navbar, Footer },
  layout () {
    return 'wizmi-base'
  }
}
</script>

<style scoped>
.layout-root {
  display: flex;
  flex-direction: column;
  min-height: calc(100vh - 16px);
  padding: 8px;
}
</style>
