<template>
  <div
    class="bg-[#0F0F10] min-h-screen bg-cover"
    
  >
    <div class="py-8 px-24">
      <div class="items-center flex mb-2 space-x-6">
        <h1 class="text-5xl font-halvar_bold text-white uppercase">AZURA</h1>
        <div class="flex justify-end space-x-4">
          <button
            @click="savePreferences()"
            type="button"
            class="
              inline-flex
              items-center
              justify-center
              px-2.5
              py-1.5
              border border-transparent
              text-sm
              font-medium
              rounded-lg
              space-x-2
              text-indigo-700
              bg-indigo-100
              hover:bg-indigo-200
              focus:outline-none
              focus:ring-2
              focus:ring-offset-2
              focus:ring-indigo-500
            "
          >
            <SaveIcon class="h-5 w-5 mr-1" />
            Save changes
          </button>
          <NuxtLink
            to="/actions"
            class="
              inline-flex
              items-center
              px-3
              py-2
              border border-gray-300
              shadow-sm
              text-sm
              leading-4
              font-medium
              rounded-lg
              text-gray-700
              bg-white
              hover:bg-gray-50
              focus:outline-none
              focus:ring-2
              focus:ring-offset-2
              focus:ring-indigo-500
            "
          >
            <svg
              fill="currentColor"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 30 30"
              class="h-5 w-5 mr-1"
            >
              <path
                d="M 6 4 L 4 8 L 4 24 L 9 24 L 9 27 L 13 27 L 16 24 L 20 24 L 26 18 L 26 4 L 6 4 z M 8 6 L 24 6 L 24 17 L 21 20 L 15 20 L 12 23 L 12 20 L 8 20 L 8 6 z M 13 9 L 13 16 L 15 16 L 15 9 L 13 9 z M 17 9 L 17 16 L 19 16 L 19 9 L 17 9 z"
              /></svg
            >Configure actions
          </NuxtLink>
        </div>
      </div>
      <div class="flex justify-center items-center">
        <div
          class="
            grid
            gap-4
            grid-rows-3 grid-cols-5 grid-flow-col
            w-full
            max-h-[950px]
          "
        >
          <div
            class="
              row-span-3
              col-span-3
              rounded-lg
              items-center
              justify-center
              max-h-[950px]
            "
          >
            <!-- <img
              src="https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9e/Azura_Lady_of_the_Lake_Face.webp?version=c71d015ced79cac659d7b4bd5d2baf31"
              class="max-h-[900px] -translate-y-16"
              alt=""
            /> -->

            <div
              class="h-full w-full bg-contain bg-top bg-no-repeat bg-tr"
              :style="{
                'background-image': outfits.find((o) => o.id === defaultOutfit)
                  .src,
              }"
            ></div>
          </div>
          <div
            class="
              items-center
              flex
              col-span-2
              bg-white/25
              backdrop-blur-md
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
                      outfit.unlocked ? 'hover:bg-white/20' : 'bg-black/70',
                      'h-full w-full transition-colors items-end flex flex-col justify-between',
                    ]"
                  >
                    <div class="items-center justify-end flex p-2">
                      <LockClosedIcon
                        v-if="!outfit.unlocked"
                        class="h-4 w-4 text-gray-500"
                      />
                    </div>
                    <div class="backdrop-blur-md bg-black/40 w-full">
                      <div
                        v-if="outfit.unlocked"
                        class="flex w-full p-2 items-center"
                      >
                        <input
                          :id="outfit.id"
                          name="notification-method"
                          type="radio"
                          :checked="outfit.id === 'email'"
                          class="
                            focus:ring-indigo-500
                            h-4
                            w-4
                            text-indigo-600
                            border-gray-300
                          "
                        />
                        <label
                          :for="outfit.id"
                          class="ml-3 block text-sm font-medium text-white"
                        >
                          {{ outfit.name }}
                        </label>
                      </div>
                      <div
                        v-else
                        class="flex w-full p-2 items-center justify-center"
                      >
                        <button
                          @click="purchaseOutfit(outfit.id, outfit.cost)"
                          class="
                            text-white
                            bg-slate-600
                            px-2
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
                <!-- <a class=""
                  ><ChevronDownIcon
                    :class="[
                      defaultOutfit === outfit.id
                        ? 'text-white cursor-pointer'
                        : 'opacity-0',
                      'h-5 w-5',
                    ]"
                /></a> -->
              </div>
            </div>
          </div>
          <!-- <div
            class="col-span-2 rounded-lg border border-white/25 text-white flex"
          >
            <dl
              class="
                grid grid-cols-1
                rounded-lg
                bg-white/25
                backdrop-blur-md
                overflow-hidden
                shadow
                divide-y divide-gray-200
                md:grid-cols-3 md:divide-y-0 md:divide-x
              "
            >
              <div
                v-for="item in stats"
                :key="item.name"
                class="px-4 py-5 sm:p-6 flex flex-col justify-center"
              >
                <dt class="text-base font-normal text-gray-900">
                  {{ item.name }}
                </dt>
                <dd
                  class="
                    mt-1
                    flex
                    justify-between
                    items-baseline
                    md:block
                    lg:flex
                  "
                >
                  <div
                    class="
                      flex
                      items-baseline
                      text-2xl
                      font-semibold
                      text-indigo-600
                    "
                  >
                    {{ item.stat }}
                    <span class="ml-2 text-sm font-medium text-gray-500">
                      from {{ item.previousStat }}
                    </span>
                  </div>

                  <div
                    :class="[
                      item.changeType === 'increase'
                        ? 'bg-green-100 text-green-800'
                        : 'bg-red-100 text-red-800',
                      'inline-flex items-baseline px-2.5 py-0.5 rounded-full text-sm font-medium md:mt-2 lg:mt-0',
                    ]"
                  >
                    <ArrowSmUpIcon
                      v-if="item.changeType === 'increase'"
                      class="
                        -ml-1
                        mr-0.5
                        flex-shrink-0
                        self-center
                        h-5
                        w-5
                        text-green-500
                      "
                      aria-hidden="true"
                    />
                    <ArrowSmDownIcon
                      v-else
                      class="
                        -ml-1
                        mr-0.5
                        flex-shrink-0
                        self-center
                        h-5
                        w-5
                        text-red-500
                      "
                      aria-hidden="true"
                    />
                    <span class="sr-only">
                      {{
                        item.changeType === "increase"
                          ? "Increased"
                          : "Decreased"
                      }}
                      by
                    </span>
                    {{ item.change }}
                  </div>
                </dd>
              </div>
            </dl>
          </div> -->
          <div class=""></div>
        </div>
      </div>
    </div>
    <SavePrefs :show-save="showSave"/>
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
              bg-black
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
                  bg-black
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
                          <span
                            class="text-4xl tracking-tight font-bold mr-2"
                            >{{ tier.coins }}</span
                          >
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
  </div>
</template>

<script setup>
import { ref } from "vue";
import {
  Disclosure,
  DisclosureButton,
  DisclosurePanel,
  Menu,
  MenuButton,
  MenuItem,
  MenuItems,
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import {
  BellIcon,
  MenuIcon,
  XIcon,
  TranslateIcon,
  ExclamationIcon,
  CheckIcon,
  ChevronDownIcon,
} from "@heroicons/vue/outline";

import {
  ClipboardCopyIcon,
  LogoutIcon,
  UserCircleIcon,
  LockClosedIcon,
  CheckCircleIcon,
  CashIcon,
  ColorSwatchIcon,
  StarIcon,
  ArrowSmDownIcon,
  ArrowSmUpIcon,
  SaveIcon,
  ChatAltIcon,
} from "@heroicons/vue/solid";

const stats = [
  {
    name: "Total Subscribers",
    stat: "71,897",
    previousStat: "70,946",
    change: "12%",
    changeType: "increase",
  },
  {
    name: "Avg. Open Rate",
    stat: "58.16%",
    previousStat: "56.14%",
    change: "2.02%",
    changeType: "increase",
  },
  {
    name: "Avg. Click Rate",
    stat: "24.57%",
    previousStat: "28.62%",
    change: "4.05%",
    changeType: "decrease",
  },
];

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

const route = useRoute();
</script>

<script>
export default {
  data() {
    return {
      open: ref(false),
      showSave: ref(false),
      balance: 100,
      defaultOutfit: "outfit_2",
      tiers: [
  {
    name: "Hobby",
    href: "#",
    priceMonthly: 4.99,
    coins: 3000,
    image: "@/assets/images/23.png",
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
    image: "@/assets/images/24.png",
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
    image: "@/assets/images/25.png",
    description: "All the basics for starting a new business",
    includedFeatures: [
      "Potenti felis, in cras at at ligula nunc. ",
      "Orci neque eget pellentesque.",
      "Donec mauris sit in eu tincidunt etiam.",
      "Faucibus volutpat magna.",
    ],
  },
],
      outfits: [
        {
          name: "Outfit 1",
          unlocked: true,
          cost: 10000,
          id: "outfit_1",
          src: "url(https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9c/Anna_Wealth-Wisher_Face.webp?version=596c36b8c62ae3f6ecc43535ee280b84)",
        },
        {
          name: "Outfit 2",
          unlocked: true,
          cost: 2000,
          id: "outfit_2",
          src: "url(https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9e/Azura_Lady_of_the_Lake_Face.webp?version=c71d015ced79cac659d7b4bd5d2baf31)",
        },
        {
          name: "Outfit 3",
          unlocked: true,
          cost: 100000,
          id: "outfit_3",
          src: "url(https://cdn.wallpapersafari.com/30/33/fIpGAw.jpg)",
        },
        {
          name: "Outfit 3",
          unlocked: false,
          cost: 100000,
          id: "outfit_4",
          src: "url(https://cdn.wallpapersafari.com/30/33/fIpGAw.jpg)",
        },
        {
          name: "Outfit 3",
          unlocked: false,
          cost: 100000,
          id: "outfit_3",
          src: "url(https://cdn.wallpapersafari.com/30/33/fIpGAw.jpg)",
        },
        {
          name: "Outfit 3",
          unlocked: false,
          cost: 100000,
          id: "outfit_4",
          src: "url(https://cdn.wallpapersafari.com/30/33/fIpGAw.jpg)",
        },
      ],
    };
  },
  methods: {
    setDefault(value) {
      this.defaultOutfit = value;
    },
    purchaseOutfit(id,cost) {
      if (this.balance < cost) this.open = true;
    },
    savePreferences() {
      this.showSave = true;
      setTimeout(() => {
        this.showSave = false;
      }, 3000);
    },
  },
};
</script>