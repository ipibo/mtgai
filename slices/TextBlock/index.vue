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
    <div class="bg-black w-[400px] h-full rounded-lg flex flex-col ">
      <div class="bg-gray-200 rounded-lg text-center py-2 m-2 drop-shadow-lg">
        {{ slice.primary.title[0].text }}
      </div>
      <div class="m-4 bg-indigo-100 rounded-lg p-2 ">{{slice.primary.information[0].text}}</div>
    </div>
  </section>
</template>
