<script setup lang="ts">
import { type Content } from "@prismicio/client"

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.TextBlockSlice>([
    "slice",
    "index",
    "slices",
    "context",
  ])
)
</script>

<template>
  <section
    :data-slice-type="slice.slice_type"
    :data-slice-variation="slice.variation"
  >
    <!-- Placeholder component for text_block (variation: {{ slice.variation }})
    Slices -->
    <div class="font-mono  h-full rounded-lg flex flex-col items-center  ">
      <div class="bg-indigo-200 font-extrabold px-4 rounded-lg text-center py-2 m-4 drop-shadow-lg text-4xl drop-shadow-lg">
        {{ slice.primary.title[0].text }}
      </div>
      <div v-for="item in slice.items" :key="item.text" class="font-thin max-w-screen-lg mx-4 my-2 bg-indigo-100 rounded-lg p-2 drop-shadow-lg ">
      
        {{item.information_paragraph[0].text}}
      
      </div>
      

      <!-- <PrismicRichText :field="item.information_paragraph" /> -->
    </div>
  </section>
</template>
