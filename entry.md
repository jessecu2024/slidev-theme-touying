---
theme: .
layout: default
routerMode: hash
---

# slidev-theme-touying

This is a Slidev theme inspired by the style of [Touying](https://touying-typ.github.io/).

Choose one of four original presentation systems:

- <a :href="getUrl('harbour')" class="text-primary">Harbour</a>
- <a :href="getUrl('sandstone')" class="text-primary">Sandstone</a>
- <a :href="getUrl('studio')" class="text-primary">Studio</a>
- <a :href="getUrl('sydney')" class="text-primary">Sydney</a>

<script setup>
function getUrl(preset) {
  return `${import.meta.env.BASE_URL}${preset}/`
}
</script>
