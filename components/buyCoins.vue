<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <TransitionRoot as="template" :show="open">
    <Dialog as="div" class="relative z-10" @close="open = false">
      <TransitionChild
        as="template"
        enter="ease-out duration-300"
        enter-from="opacity-0"
        enter-to="opacity-100"
        leave="ease-in duration-200"
        leave-from="opacity-100"
        leave-to="opacity-0"
      >
        <div
          class="
            fixed
            inset-0
            bg-gray-900
            backdrop-blur-sm
            bg-opacity-75
            transition-opacity
          "
        />
      </TransitionChild>

      <div class="fixed z-10 inset-0 overflow-y-auto">
        <div
          class="
            flex
            items-end
            sm:items-center
            justify-center
            min-h-full
            p-4
            text-center
            sm:p-0
          "
        >
          <TransitionChild
            as="template"
            enter="ease-out duration-300"
            enter-from="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
            enter-to="opacity-100 translate-y-0 sm:scale-100"
            leave="ease-in duration-200"
            leave-from="opacity-100 translate-y-0 sm:scale-100"
            leave-to="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
          >
            <DialogPanel
              class="
                relative
                bg-[#231739]
                rounded-lg
                px-4
                pt-5
                pb-4
                overflow-hidden
                shadow-xl
                transform
                transition-all
                sm:my-8 sm:w-fit sm:p-6
              "
            >
              <div
                class="
                  bg-yellow-50
                  border-l-4 border-yellow-400
                  p-4
                  flex
                  justify-between
                  items-center
                "
              >
                <div class="flex">
                  <div class="flex-shrink-0">
                    <ExclamationIcon
                      class="h-5 w-5 text-yellow-400"
                      aria-hidden="true"
                    />
                  </div>
                  <div class="ml-3">
                    <p class="text-sm text-yellow-700">
                      You have insufficient credits left.
                      {{ " " }}
                      <span
                        class="
                          font-medium
                          underline
                          text-yellow-700
                          hover:text-yellow-600
                        "
                      >
                        Buy a pack to add more credits.
                      </span>
                    </p>
                  </div>
                </div>
                <button
                  type="button"
                  class="
                    rounded-md
                    text-yellow-600
                    hover:text-yellow-700
                    focus:outline-none focus:ring-0 focus:ring-offset-0
                  "
                  @click="open = false"
                >
                  <span class="sr-only">Close</span>
                  <XIcon class="h-6 w-6" aria-hidden="true" />
                </button>
              </div>
              <div class="flex space-x-4 mt-8">
                <div
                  v-for="tier in tiers"
                  :key="tier.name"
                  class="
                    border border-[#E7D8FF]/50
                    bg-[#E7D8FF]/20
                    rounded-lg
                    shadow-sm
                    divide-y divide-gray-200
                  "
                >
                  <div class="p-6 text-center">
                    <div
                      class="
                        mt-4
                        flex flex-col
                        items-center
                        justify-center
                        font-halvar_bold
                        text-[#E7D8FF]
                      "
                    >
                      <img :src="tier.image" class="w-36" alt="" />
                      <div class="flex items-center justify-center">
                        <span class="text-4xl tracking-tight font-bold mr-2">{{
                          tier.coins
                        }}</span>
                        {{ " " }}
                        <CashIcon class="h-8 w-8" />
                      </div>
                    </div>
                    <a
                      :href="tier.href"
                      class="
                        mt-8
                        block
                        font-halvar
                        w-full
                        bg-[#703ED9]/70
                        border border-[#703ED9]
                        rounded-md
                        py-2
                        text-lg text-white text-center
                        hover:bg-gray-900
                      "
                      >${{ tier.priceMonthly }}</a
                    >
                  </div>
                </div>
              </div>
            </DialogPanel>
          </TransitionChild>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>
</template>

<script setup>
import { ref } from "vue";
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import { ExclamationIcon, XIcon, CheckIcon } from "@heroicons/vue/outline";
import { CashIcon } from "@heroicons/vue/solid";
const tiers = [
  {
    name: "Hobby",
    href: "#",
    priceMonthly: 4.99,
    coins: 3000,
    image: "../assets/images/23.png",
    description: "All the basics for starting a new business",
    includedFeatures: [
      "Potenti felis, in cras at at ligula nunc.",
      "Orci neque eget pellentesque.",
    ],
  },
  {
    name: "Freelancer",
    href: "#",
    priceMonthly: 9.99,
    coins: 10000,
    image: "../assets/images/24.png",
    description: "All the basics for starting a new business",
    includedFeatures: [
      "Potenti felis, in cras at at ligula nunc. ",
      "Orci neque eget pellentesque.",
      "Donec mauris sit in eu tincidunt etiam.",
    ],
  },
  {
    name: "Startup",
    href: "#",
    priceMonthly: 24.99,
    coins: 25000,
    image: "../assets/images/25.png",
    description: "All the basics for starting a new business",
    includedFeatures: [
      "Potenti felis, in cras at at ligula nunc. ",
      "Orci neque eget pellentesque.",
      "Donec mauris sit in eu tincidunt etiam.",
      "Faucibus volutpat magna.",
    ],
  },
];
</script>

<script>
export default {
  props: ["open"],
};
</script>