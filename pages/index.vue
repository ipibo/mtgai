<script setup lang="ts">
import { components } from "~/slices"

const prismic = usePrismic()
const { data: page } = useAsyncData("index", () =>
  prismic.client.getByUID("page", "home")
)

useHead({
  title: prismic.asText(page.value?.data.title),
})



</script>

<template>
  <div>
    <SliceZone
      wrapper="main"
      :slices="page?.data.slices ?? []"
      :components="components"
    />

    <!-- <p>info about your card: {{ card.name }}</p> -->
    <!-- {{ card.image_uris.normal }} -->

    <!-- <img :src="card.image_uris.small" alt=""> -->

  
  </div>
</template>
