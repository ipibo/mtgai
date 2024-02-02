<script setup lang="ts">
import { type Content } from "@prismicio/client"

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.CardSelectorBlockSlice>([
    "slice",
    "index",
    "slices",
    "context",
  ])
)
const searchCard = async () => {
  console.log(cardName.value)
  foundCard.value = await useFetch(
    `https://api.scryfall.com/cards/named?fuzzy=${cardName.value}`
  ).then((res) => {
    // console.log(res.data)
    // console.log(res.data.value.image_uris.small)
    // console.log(res.data.value.name)
    return res.data
  })
}

const foundCard = ref()
const cardName = ref("")
</script>

<template>
  <section
    :data-slice-type="slice.slice_type"
    :data-slice-variation="slice.variation"
  >

    
    <div class="font-mono flex flex-col mt-10 items-center">
      
      <div class="font-bold mb-2">Search for you card</div>

      <div class="flex flex-row gap-2 mb-2">
        <input
          class="bg-white text-black drop-shadow-lg p-4 rounded-md"
          type="text"
          v-model="cardName"
        />

        <button
          class="rounded-md bg-indigo-200 p-4 drop-shadow-lg"
          @click="searchCard"
        >
          search
        </button>
      </div>

      <div
        v-if="foundCard"
        class="max-w-screen-sm p-4 rounded-md bg-indigo-200"
      >
        <div class="flex flex-row gap-2">
          <div>{{ foundCard.value.name }}</div>
          <div>{{ foundCard.value.mana_cost }}</div>
        </div>
        <div class="font-bold">{{ foundCard.value.type_line }}</div>
        <div class="mt-2">{{ foundCard.value.oracle_text }}</div>
        <div class="flex flex-row gap-2">
          {{ foundCard.value.power }} /
          {{ foundCard.value.toughness }}
        </div>
        <img :src="foundCard.value.image_uris.small" alt="" />
        <a :href="foundCard.value.scryfall_uri">Link to scryfall</a>
      </div>
    </div>
  </section>
</template>
