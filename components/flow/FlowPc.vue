<template>
  <div :class="$style.FlowCard">
    <div :class="$style.FirstSectionWrapper">
      <h3>{{ $t('新型コロナウイルス感染症にかかる相談窓口について') }}</h3>
      <div :class="[$style.Outer, $style.OuterUpper]">
        <div :class="[$style.CardBlock, $style.Past]">
          <div :class="[$style.CardBlockInner]">
            <flow-pc-past />
            <img
              :class="$style.CardBlockIcon"
              src="/flow/flow_arrow.svg"
              aria-hidden="true"
              alt=" "
            />
          </div>
        </div>
        <div :class="[$style.CardBlock, $style.Days]">
          <div class="[$style.CardBlockInner]">
            <flow-pc-days />
            <img
              :class="$style.CardBlockIcon"
              src="/flow/flow_arrow.svg"
              aria-hidden="true"
              alt=" "
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import FlowPcPast from './FlowPcPast.vue'
import FlowPcDays from './FlowPcDays.vue'

export default {
  components: {
    FlowPcPast,
    FlowPcDays
  }
}
</script>

<style module lang="scss">
.FirstSectionWrapper {
  page-break-before: avoid;
  page-break-inside: avoid;
  > h3 {
    color: $gray-2;
    font-size: 1.5rem;
    margin-bottom: 7px;
    @media print {
      display: none;
    }
  }
}

.FlowCard {
  display: flex;
  flex-direction: column;
  background: white;
  border-radius: 4px;
  padding: 10px 20px;
  margin-bottom: 20px;
  word-break: break-word;
  hyphens: auto;
  @media print {
    padding: 10px 20px 0 20px;
    margin-bottom: 0;
  }

  &GrayBg {
    background-color: $gray-5;
  }
}

.Outer {
  $grid-gap: 12px;

  display: grid;

  &Upper {
    grid-gap: $grid-gap;
    grid-template-columns: 70% 30%;
    -ms-grid-columns: 70% 12px 30%;
    grid-template-rows: repeat(3, auto);
    -ms-grid-rows: auto 12px auto 12px auto;

    & > *:nth-child(1) {
      -ms-grid-column: 1;
      -ms-grid-row: 1;
    }

    & > *:nth-child(2) {
      -ms-grid-column: 1;
      -ms-grid-row: 3;
    }

    & > *:nth-child(3) {
      -ms-grid-column: 1;
      -ms-grid-row: 5;
    }

    & > *:nth-child(4) {
      -ms-grid-column: 3;
      -ms-grid-row: 1;
      -ms-grid-row-span: 3;
    }

    & > *:nth-child(5) {
      -ms-grid-column: 3;
      -ms-grid-row: 5;
    }

    margin-bottom: 36px;
  }

  .CardBlock {
    &Inner {
      position: relative;
    }

    &Icon {
      position: absolute;
      bottom: 10%;
      right: -30px;
      z-index: 1;
    }

    &Suspect {
      .CardBlockIcon {
        bottom: 40%;
      }
    }

    &required {
      .CardBlockIcon:nth-of-type(1) {
        top: auto;
        bottom: -30px;
        right: auto;
        left: 22%;
        margin-top: 0;
        transform: rotate(90deg);
      }
      .CardBlockIcon:nth-of-type(2) {
        top: auto;
        bottom: 12%;
        right: -30px;
        margin-top: 0;
      }
    }
  }
}
</style>
