<template>
  <div class="px-4 sm:px-6 lg:px-8 py-6">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto flex items-center space-x-4">
        <h1 class="text-xl font-semibold text-white">Gestures</h1>
        <NuxtLink
          to="../"
          class="
            inline-flex
            items-center
            justify-center
            px-2.5
            py-1.5
            border border-purple-600
            text-sm
            font-medium
            rounded-lg
            space-x-2
            text-purple-200
            bg-purple-700
            hover:bg-purple-600
            focus:outline-none
            focus:ring-2
            focus:ring-offset-2
            focus:ring-purple-500
          "
        >
          <ColorSwatchIcon class="h-5 w-5 mr-1" />
          Edit waifu
        </NuxtLink>
      </div>
    </div>
    <div class="mt-8 flex flex-col">
      <div class="overflow-x-auto">
        <div class="inline-block min-w-full py-2 align-middle">
          <div class="overflow-hidden shadow ring-1 ring-black ring-opacity-5">
            <div
              class="
                items-center
                flex
                col-span-2
                rounded-lg
                overflow-auto
                whitespace-nowrap
              "
            >
              <div
                class="
                  flex
                  items-center
                  justify-center
                  space-x-1
                  h-auto
                  font-halvar_bold
                  uppercase
                "
              >
                <div
                  v-for="outfit in outfits"
                  :key="outfit.id"
                  class="flex flex-col justify-center items-center h-72 w-36"
                >
                  <div
                    :class="[
                      defaultOutfit === outfit.id ? '' : '',
                      'h-full w-full  bg-white/50 bg-cover bg-center',
                    ]"
                    :style="{ 'background-image': outfit.src }"
                    @click="setDefault(outfit.id)"
                    :disabled="!outfit.unlocked"
                  >
                    <div
                      :class="[
                        outfit.unlocked ? '' : 'bg-black/70',
                        'h-full w-full transition-colors items-end flex flex-col justify-between',
                      ]"
                    >
                      <div class="items-center justify-end flex p-2">
                        <LockClosedIcon
                          v-if="!outfit.unlocked"
                          class="h-4 w-4 text-gray-500"
                        />
                      </div>
                      <div
                        :class="[
                          outfit.unlocked ? 'backdrop-blur-md bg-black/40' : '',
                          ' w-full p-2',
                        ]"
                      >
                        <div
                          v-if="outfit.unlocked"
                          class="flex w-full items-center"
                        >
                          <div
                            :for="outfit.id"
                            class="ml-3 block text-sm font-medium text-white"
                          >
                            {{ outfit.name }}
                          </div>
                        </div>
                        <div
                          v-else
                          class="flex w-full items-center justify-center"
                        >
                          <button
                            @click="purchaseOutfit(outfit.id, outfit.cost)"
                            class="
                              text-white
                              bg-slate-600
                              px-2
                              py-0
                              rounded
                              hover:bg-slate-500
                            "
                          >
                            {{ outfit.cost }}
                          </button>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ColorSwatchIcon } from "@heroicons/vue/solid";
const outfits = [
  {
    name: "The Floss",
    unlocked: true,
    cost: 10000,
    id: "outfit_1",
    src: "url(https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9e/Azura_Lady_of_the_Lake_Face.webp?version=c71d015ced79cac659d7b4bd5d2baf31)",
  },
  {
    name: "Outfit 2",
    unlocked: false,
    cost: 2000,
    id: "outfit_2",
    src: "url(https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9e/Azura_Lady_of_the_Lake_Face.webp?version=c71d015ced79cac659d7b4bd5d2baf31)",
  },
  {
    name: "The Floss",
    unlocked: true,
    cost: 10000,
    id: "outfit_1",
    src: "url(https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9e/Azura_Lady_of_the_Lake_Face.webp?version=c71d015ced79cac659d7b4bd5d2baf31)",
  },
];
</script>

<script>
export default {
  data() {
    return {};
  },
  computed: {
    abbreviatedNumber(number) {
      let SI_SYMBOL = ["", "k", "M", "B", "T", "P", "E"];
      let tier = (Math.log10(Math.abs(Math.floor(number))) / 3) | 0;
      if (tier == 0) {
        return Math.floor(number);
      } else {
        let suffix = SI_SYMBOL[tier];
        let scale = Math.pow(10, tier * 3);
        let scaled = number / scale;
        let length = scaled.toFixed(1).toString().length;
        let precision = length > 4 ? 0 : 1;
        return scaled.toFixed(precision) + suffix;
      }
    },
  },
};
</script>