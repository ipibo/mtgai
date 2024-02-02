<script setup lang="ts">
import { type Content } from "@prismicio/client"

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.QuestionBlockSlice>([
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
    <!-- Placeholder component for question_block (variation: {{ slice.variation }})
    Slices  -->
    <div class="font-mono flex flex-col  mt-10 items-center">
      <div class="bg-indigo-100 p-10 rounded-lg drop-shadow-lg max-w-screen-2xl ">
        <h1 class="text-center text-black text-2xl mb-2">
          {{ slice.primary.title }}
        </h1>

        <form class="flex flex-col gap-2" action="">
          <label for="question" />
          <textarea
            id="question"
            class="rounded-md bg-white-100 p-2"
            name="question"
            cols="30"
            rows="10"
            placeholder="your mtg related question"
          />
          <button class="bg-white rounded-md p-2 drop-shadow-lg" type="submit">
            Submit
          </button>
        </form>
      </div>
    </div>
  </section>
</template>
