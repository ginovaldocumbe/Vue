<script >
import Header from "./header.vue";
import Card from "./card.vue";
import Footer from "./footer.vue";
export default {
  components: {
    Header,
    Footer,
    Card
  }
}
</script>

<template>
  <div class="custom-shape-divider-top-1662394809">
    <svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
      <path d="M1200 120L0 16.48 0 0 1200 0 1200 120z" class="shape-fill"></path>
    </svg>
  </div>
  <section>
    <Header />
    <Card />
    <Footer />
  </section>
</template>

<style scoped>
section {
  display: flex;
  padding-top: 10%;
  height: 100vh;
  flex-direction: column;
  justify-content: space-between !important;
  align-items: center;
}

.custom-shape-divider-top-1662394809 {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  overflow: hidden;
  line-height: 0;
  z-index: -1;
}

.custom-shape-divider-top-1662394809 svg {
  position: relative;
  display: block;
  width: calc(300% + 1.3px);
  height: 400px;
  transform: rotateY(180deg);
}

.custom-shape-divider-top-1662394809 .shape-fill {
  fill: #2c032c;
}
</style>
