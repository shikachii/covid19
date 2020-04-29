<template>
  <div :class="$style.FlowCard">
    <h3 :class="['mb-4', $style.FlowCardHeading]">
      {{ $t('新型コロナウイルス感染症にかかる相談窓口について') }}
    </h3>
    <div :class="$style.FlowCard">
    </div>
  </div>
</template>

<script>
import VueScrollTo from 'vue-scrollto'
// import FlowSpPast from './FlowSpPast.vue'

export default {
  components: {
//    FlowSpPast
  },
  mounted() {
    const hash = this.$route.hash
    if (hash !== '') {
      VueScrollTo.scrollTo(hash, 1000, { offset: -72})
    }
  }
}
</script>

<style module lang="scss">
.FlowCard {
  display: flex;
  flex-direction: column;

  @include card-container();

  padding: 20px;
  margin-bottom: 20px;
  word-break: break-word;
  hyphens: auto;

  > h3 {
    color: $gray-2;
    font-size: 1.5rem;
  }

  &GrayBg {
    background-color: $gray-5;
    box-shadow: none;
    border: none !important;
  }
}
</style>
