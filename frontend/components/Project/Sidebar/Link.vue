<template>
  <span>
    <a
      v-if="page.outbound"
      :href="link"
      target="_blank"
      exact-active-class="selected"
    >
      {{ page.title }}
      <i class="material-icons outboundIcon">open_in_new</i>
    </a>
    <NuxtLink
      v-else
      :to="link"
      :target="page.outbound ? '_blank' : ''"
      prefetch-on="interaction"
      exact-active-class="selected"
    >
      {{ page.title }}
    </NuxtLink>
  </span>
</template>

<script setup lang="ts">
const { page } = defineProps<{ page: SelectableLink }>()
const link = page.href.replace('.md', '')
</script>

<style lang="scss" scoped>
.outboundIcon {
  font-size: 13px;
  opacity: 0.6;
  margin-left: 3px;
}

a {
  color: #212121;
}

a:hover {
  color: #039be5;
  cursor: pointer;
}

a.selected {
  color: #039be5;
  font-weight: bold;
}
</style>
