<template>
  <div class="short">
    <span v-for="item in badgeItems" :key="item.index" class="shortcut-item hint--bottom-left" :aria-label="item.label">
      <icon-badge :iconobj="item" :id="item.name" :iconname="item.iconName" ></icon-badge>
    </span>
    <span v-for="item in shortcut" :key="item.index" class="shortcut-item hint--bottom-left" :aria-label="item.label">
      <svg class="icon"><use :xlink:href="item.iconName"></use></svg>
    </span>
    <span id="fullScreen" class="shortcut-item hint--bottom-left" aria-label="全屏">
      <svg class="icon"><use :xlink:href="isFullScreen ? '#icon-shrink' : '#icon-enlarge'"></use></svg>
    </span>
  </div>
</template>
<script>
import shortcutItems from './js/shortcut_def.js'
import iconBadge from '../components/icon-badge.vue'
export default {
  name: 'shortOper',
  data () {
    return {
      badgeItems: shortcutItems.slice(0, 2),
      shortcut: shortcutItems.slice(2),
      isFullScreen: false
    }
  },
  components: {
    'icon-badge': iconBadge
  }
}
</script>
<style lang="sass" scoped>
  @import '../style/defs.sass'
  .short
    display: flex
    border-right: 1px solid $border-color
    .shortcut-item
      margin: 0 .3rem
</style>

