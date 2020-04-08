<template>
  <div class="LanguageSelector">
    <div class="LanguageSelector-Background">
    </div>
    <select
      id="LanguageSelector"
      class="LanguageSelector-Menu"
      v-model="currentLocaleCode"
      @change="handleChangeLanguage"
    >
      <option
        v-for="locale in $root.$i18n.locales"
        :key="locale.code"
        :value="locale.code"
        :title="'Switch to ' + locale.name"
      >
        {{ locale.name }}
      </option>
    </select>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

type LocaleCode = {
  currentLocaleCode: string
}

export default Vue.extend({
  components: {
  },
  data(): LocaleCode {
    return {
      currentLocaleCode: this.$root.$i18n.locale
    }
  },
  methods: {
    handleChangeLanguage() {
      this.$root.$i18n.setLocale(this.currentLocaleCode)
    }
  }
})

</script>

<style lang="scss" scoped>
.LanguageSelector {
  position: relative;
  padding:2px 20px;
}
</style>
