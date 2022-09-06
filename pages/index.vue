
<template>
  <div>
    <div class="bg-[#0E0E10] h-screen pt-4 pb-8 static">
      <div class="flex items-center max-w-full m-auto h-[90%] px-2 mt-6">
        <div
          v-for="(character, idx) in characters"
          :key="character.id"
          :class="[
            defaultCharacter === character.name
              ? 'bg-white'
              : `${!character.unlocked ? 'bg-slate-900' : `char${idx + 1}`}`,
            'first:rounded-l-lg last:rounded-r-lg group char h-full mr-1 flex flex-1 focus:grow-[3] hover:grow-[3]',
          ]"
        >
          <img
            :src="character.src"
            :class="[
              character.unlocked
                ? `group-hover:opacity-100 ${
                    defaultCharacter === character.name
                      ? 'opacity-100'
                      : 'opacity-40'
                  }`
                : 'opacity-30 group-hover:opacity-50',
              'rounded shrink-0 absolute min-w-[900px] left-[30%] h-[150%] translate-x-[-50%] transition-all duration-500',
            ]"
            alt=""
          />
          <div
            :class="[
              character.unlocked ? 'text-black/80' : 'text-[#E7D8FF]',
              'title group-hover:opacity-100 opacity-0  font-halvar_bold text-[70px] uppercase mr-4',
            ]"
          >
            {{ character.name }}
          </div>

          <div
            v-if="!character.unlocked"
            class="flex items-center justify-items-stretch text-[#E7D8FF]"
          >
            <button
              class="
                font-halvar_bold
                text-xl
                py-4
                bg-[#120927c9]
                transition-colors
                hover:bg-[#2b1955c9]
                rounded-b
                z-0
                inset-x-0
                bottom-0
                flex
                items-center
                justify-center
                shadow-lg
                absolute
              "
              @click="purchaseCharacter(character.cost)"
            >
              <LockClosedIcon class="h-5 w-5 mr-2 opacity-60" />
              {{ character.cost }}
            </button>
          </div>
          <div
            v-else
            :class="[
              'flex space-x-2 opacity-0 group-hover:opacity-100 transition-all duration-700 absolute inset-x-2 bottom-2',
            ]"
          >
            <button
              v-if="character.name !== defaultCharacter"
              :class="[
                character.name === defaultCharacter
                  ? 'text-slate-200'
                  : 'text-slate-200',
                'font-halvar_bold text-xl h-12 w-12 py-4 transition-colors  bg-slate-600 hover:bg-slate-700 rounded-full flex items-center justify-center shadow-lg',
              ]"
              @click="selectDefault(character.name, character.unlocked)"
            >
              <StarIcon class="h-5 w-5" />
            </button>
            <NuxtLink
              v-else-if="character.name === defaultCharacter"
              :to="'/heroes/' + character.id + '/'"
              class="
                font-halvar_bold
                text-xl
                h-12
                w-12
                py-4
                transition-colors
                text-[#E7D8FF]
                bg-[#703ED9]
                hover:bg-[#55349d]
                rounded-full
                flex
                items-center
                justify-center
                shadow-lg
              "
              ><ColorSwatchIcon class="h-5 w-5"
            /></NuxtLink>
          </div>
        </div>
        <BuyCoins :open="open" />
      </div>
    </div>
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
} from "@heroicons/vue/solid";

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
      defaultCharacter: "Azura",
      open: false,
      balance: 500,
      characters: [
        {
          name: "Azura",
          id: 1,
          cost: 500,
          unlocked: true,
          default: true,
          src: "https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9e/Azura_Lady_of_the_Lake_Face.webp?version=c71d015ced79cac659d7b4bd5d2baf31",
        },
        {
          name: "Roy",
          id: 2,
          cost: 5000,
          unlocked: false,
          default: false,
          src: "https://gamepedia.cursecdn.com/feheroes_gamepedia_en/c/c6/Roy_Brave_Lion_Face.webp?version=64902fa1aaf52cc1ec5922a1e6155c49",
        },
        {
          name: "Anna",
          id: 3,
          cost: 500,
          unlocked: true,
          default: false,
          src: "https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9c/Anna_Wealth-Wisher_Face.webp?version=596c36b8c62ae3f6ecc43535ee280b84",
        },
        {
          name: "Shigure",
          id: 4,
          cost: 500,
          unlocked: true,
          default: false,
          src: "https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9d/Shigure_Dark_Sky_Singer_Face.webp?version=5a7a30accb6c8b68578c18ca16b34cb4",
        },
        {
          name: "Olivia",
          id: 5,
          cost: 500,
          unlocked: true,
          default: false,
          src: "https://gamepedia.cursecdn.com/feheroes_gamepedia_en/7/7c/Olivia_Sky-High_Dancer_Face.webp?version=4a68750e76bfc19c6c762b2180bbb3ab",
        },
      ],
    };
  },
  methods: {
    purchaseCharacter(value) {
      if (this.balance < value) this.open = true;
    },
    selectDefault(charName, unlocked) {
      if (unlocked) this.defaultCharacter = charName;
    },
  },
};
</script>

<style scoped>
.flash {
  animation: infinite;
}

.char {
  display: flex;
  box-sizing: border-box;
  transition: flex-grow ease 0.4s, background-color ease 0.4s;
  position: relative;
  z-index: 0;
  overflow: hidden;
}

.char:last-child {
  border-right: none;
}

.char .title {
  position: absolute;
  right: 0px;
  padding: 5px;
  text-align: center;
  transition: opacity ease 0.4s;
  z-index: 1;
}

.char1 {
  background-color: lightblue;
}

.char2 {
  background-color: rgb(201, 153, 255);
  background-image: radial-gradient(
      at 74% 83%,
      rgb(130, 250, 252) 0px,
      transparent 50%
    ),
    radial-gradient(at 6% 95%, rgb(221, 96, 240) 0px, transparent 50%),
    radial-gradient(at 87% 94%, rgb(81, 223, 245) 0px, transparent 50%),
    radial-gradient(at 87% 24%, rgb(149, 203, 239) 0px, transparent 50%),
    radial-gradient(at 82% 50%, rgb(145, 247, 154) 0px, transparent 50%),
    radial-gradient(at 94% 52%, rgb(228, 108, 164) 0px, transparent 50%),
    radial-gradient(at 45% 15%, rgb(116, 161, 251) 0px, transparent 50%);
}

.char3 {
  background-color: rgb(201, 153, 255);
  background-image: radial-gradient(
      at 74% 83%,
      rgb(130, 250, 252) 0px,
      transparent 50%
    ),
    radial-gradient(at 6% 95%, rgb(221, 96, 240) 0px, transparent 50%),
    radial-gradient(at 87% 94%, rgb(81, 223, 245) 0px, transparent 50%),
    radial-gradient(at 87% 24%, rgb(149, 203, 239) 0px, transparent 50%),
    radial-gradient(at 82% 50%, rgb(145, 247, 154) 0px, transparent 50%),
    radial-gradient(at 94% 52%, rgb(228, 108, 164) 0px, transparent 50%),
    radial-gradient(at 45% 15%, rgb(116, 161, 251) 0px, transparent 50%);
}

.char4 {
  background-color: rgb(255, 197, 153); background-image: radial-gradient(at 81% 27%, rgb(218, 108, 161) 0px, transparent 50%), radial-gradient(at 22% 7%, rgb(252, 217, 151) 0px, transparent 50%), radial-gradient(at 22% 10%, rgb(207, 152, 240) 0px, transparent 50%), radial-gradient(at 50% 85%, rgb(157, 212, 246) 0px, transparent 50%), radial-gradient(at 77% 29%, rgb(137, 225, 188) 0px, transparent 50%), radial-gradient(at 29% 60%, rgb(230, 91, 207) 0px, transparent 50%), radial-gradient(at 82% 38%, rgb(166, 105, 236) 0px, transparent 50%);
}

.char5 {
  background-color: #816581;
}
</style>