<template>
  <div>
    <Navbar />
    <slot />
  </div>
</template>

<script lang="ts">
import Navbar from '~~/components/WizmiNavbar.vue'

export default {
  components: { Navbar },
  layout () {
    return 'wizmi-base'
  }
}
</script>
