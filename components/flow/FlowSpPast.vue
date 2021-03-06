<template>
  <div :class="$style.container">
    <h4 :class="$style.heading">
      <i18n path="{past}の出来ごとと症状" tag="span">
        <template v-slot:past>
          <i18n :class="$style.fzLarge" tag="span" path="発症前{two}週間以内">
            <template v-slot:two>
              <span :class="$style.fzNumeric">2</span>
            </template>
          </i18n>
        </template>
      </i18n>
    </h4>
    <p :class="$style.type">
      <template v-if="!langsNeedReversedOrder.includes($i18n.locale)">
        <strong :class="$style.source">{{
          $t('「新型コロナウイルス感染者」と')
        }}</strong>
        <i18n
          tag="span"
          path="{closeContact}をした方"
          :class="[$style.behavior, $style.fzXLarge]"
        >
          <template v-slot:closeContact>
            <em :class="$style.underline">{{ $t('濃厚接触') }}</em>
          </template>
        </i18n>
      </template>
      <template v-else>
        <i18n
          tag="span"
          path="{closeContact}をした方"
          :class="[$style.behavior, $style.fzXLarge]"
        >
          <template v-slot:closeContact>
            <em :class="$style.underline">{{ $t('濃厚接触') }}</em>
          </template>
        </i18n>
        <strong :class="$style.source">{{
          $t('「新型コロナウイルス感染者」と')
        }}</strong>
      </template>
    </p>
    <div :class="[$style.rectContainer, $style.req]">
      <p :class="$style.symptom">
        {{ $t('発熱') }}
      </p>
      <p :class="$style.op">
        {{ $t('または') }}
      </p>
      <p :class="$style.symptom">
        {{ $t('呼吸器症状') }}
      </p>
    </div>
    <p :class="[$style.type, $style.hr]">
      <template v-if="!langsWithoutFlowTitle.includes($i18n.locale)">
        <strong :class="$style.source">{{
          $t('流行地域への渡航・居住歴がある方')
        }}</strong>
        <i18n
          tag="span"
          path="{you} か {closeContact}をした方"
          :class="[$style.behavior, $style.fzXLarge]"
        >
          <template v-slot:you>
            <em :class="$style.underline">{{ $t('ご本人') }}</em>
          </template>
          <template v-slot:closeContact>
            <em :class="$style.underline">{{ $t('濃厚接触') }}</em>
          </template>
        </i18n>
      </template>
    </p>
    <div :class="[$style.rectContainer, $style.req]">
      <p :class="$style.symptom">
        {{ $t('呼吸器症状') }}
      </p>
      <p :class="$style.op">
        {{ $t('かつ') }}
      </p>
      <p :class="$style.symptom">
        <i18n tag="span" path="発熱{temperature}" :class="$style.fzSmall">
          <template v-slot:temperature>
            <i18n
              tag="span"
              path="{tempNum}以上"
              :class="[$style.break, $style.fzRegular]"
            >
              <template v-slot:tempNum>
                <span :class="$style.temp">{{ $t('37.5℃') }}</span>
              </template>
            </i18n>
          </template>
        </i18n>
      </p>
    </div>
    <a
      v-scroll-to="{
        el: '#consult',
        onDone: onDoneScroll
      }"
      href="#consult"
      :class="[$style.button, $style.clickable]"
    >
      <span :class="$style.text">{{ $t('新型コロナ受診相談窓口へ') }}</span>
      <arrow-forward-icon :class="$style.icon" />
    </a>
  </div>
</template>

<script lang="ts">
import { onDoneScroll } from '@/utils/vueScrollTo'
import ArrowForwardIcon from '@/static/flow/arrow_forward-24px.svg'

export default {
  components: { ArrowForwardIcon },
  computed: {
    langsNeedReversedOrder() {
      return ['en']
    },
    langsWithoutFlowTitle() {
      return ['en']
    }
  },
  methods: { onDoneScroll }
}
</script>

<style module lang="scss">
@import '@/components/flow/flow_sp.scss';

.type {
  margin-top: px2vw(20);
  text-align: center;

  &.hr {
    margin-top: px2vw(30);
    padding-top: px2vw(30);
    border-top: 1px $gray-4 solid;
  }

  .source {
    display: block;
    color: $purple-1;

    &:last-child {
      margin-top: px2vw(10);
    }
  }

  .behavior {
    display: block;

    &:last-child {
      margin-top: px2vw(5);
    }
  }
}

.rectContainer {
  .op {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  &.req {
    margin-top: px2vw(20);

    > .symptom {
      flex-basis: 36%;
    }

    > .op {
      flex-basis: 28%;
      margin-top: px2vw(30);
      padding: px2vw(15) px2vw(15) px2vw(10);
    }
  }
}

@include largerThan($small) {
  $vw: 960;

  .type {
    margin-top: px2vw(20, $vw);

    &.hr {
      margin-top: px2vw(30, $vw);
      padding-top: px2vw(30, $vw);
    }

    .source {
      &:last-child {
        margin-top: px2vw(10, $vw);
      }
    }

    .behavior {
      &:last-child {
        margin-top: px2vw(5, $vw);
      }
    }
  }

  .rectContainer {
    &.req {
      margin-top: px2vw(20, $vw);

      > .op {
        flex-basis: 20%;
        margin-top: px2vw(30, $vw);
        padding: px2vw(15, $vw) px2vw(15, $vw) px2vw(10, $vw);
      }
    }
  }
}
</style>
