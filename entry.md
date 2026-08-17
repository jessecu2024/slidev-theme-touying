---
theme: .
layout: default
routerMode: hash
---

# slidev-theme-touying

This is a Slidev theme inspired by the style of [Touying](https://touying-typ.github.io/).

Choose a Touying port or the Sydney editorial preset:

- <a :href="getUrl('dewdrop')" class="text-primary">Dewdrop</a>
- <a :href="getUrl('university')" class="text-primary">University</a>
- <a :href="getUrl('simple')" class="text-primary">Simple</a>
- <a :href="getUrl('sydney')" class="text-primary">Sydney</a>

<script setup>
function getUrl(preset) {
  return `${import.meta.env.BASE_URL}${preset}/`
}
</script>
