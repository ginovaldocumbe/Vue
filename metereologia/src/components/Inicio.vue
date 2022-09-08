<script>
import top from "./top.vue"
import foote from "./footer.vue"
import cards from "./cards.vue"

export default {
  name: "Inicio",
  components: {
    top,
    foote,
    cards
  },
}

</script>

<template>
  <div>
    <top />
    <cards />
    <foote />
  </div>
</template>

<style>

</style>

