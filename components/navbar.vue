<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <Disclosure as="nav" class="bg-[#18191A] py-2" v-slot="{ open }">
    <div class="max-w-7xl mx-auto px-2 sm:px-6 lg:px-10">
      <div class="relative flex items-center justify-between h-16">
        <div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
          <!-- Mobile menu button-->
          <DisclosureButton
            class="
              inline-flex
              items-center
              justify-center
              p-2
              rounded-md
              text-gray-400
              hover:text-white hover:bg-gray-700
              focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white
            "
          >
            <span class="sr-only">Open main menu</span>
            <MenuIcon v-if="!open" class="block h-6 w-6" aria-hidden="true" />
            <XIcon v-else class="block h-6 w-6" aria-hidden="true" />
          </DisclosureButton>
        </div>
        <div
          class="
            flex-1 flex
            items-center
            justify-center
            sm:items-stretch sm:justify-start
          "
        >
          <div class="flex-shrink-0 flex items-center">
            <img
              class="block lg:hidden h-8 w-auto"
              src="../assets/images/logo.png"
              alt="Workflow"
            />
            <img
              class="hidden lg:block h-8 w-auto"
              src="../assets/images/logo.png"
              alt="Workflow"
            />
          </div>
          <div class="hidden sm:block sm:ml-6 items-center font-halvar">
            <div class="flex space-x-4 uppercase items-center text-sm">
              <button
                class="
                  block
                  border
                  h-12
                  w-12
                  truncate
                  border-[#703ED9]
                  text-[#703ED9]
                  hover:bg-[#0F071F]
                  rounded-xl
                  mx-6
                "
                @click="changeLang()"
              >
                {{ language }}
              </button>

              <NuxtLink
                v-for="item in navigation"
                :key="item.name"
                :to="item.href"
                :class="[
                  route.path === item.href
                    ? ' text-[#E7D8FF] border-b-2 border-[#E7D8FF]'
                    : 'text-[#9A8EAE] border-b-2 border-transparent hover:border-[#9A8EAE] ',
                  'px-3 py-2 text-sm font-medium transition-colors',
                ]"
                >{{ item.name }}</NuxtLink
              >
            </div>
          </div>
        </div>
        <div
          class="
            absolute
            inset-y-0
            right-0
            flex
            items-center
            pr-2
            sm:static sm:inset-auto sm:ml-6 sm:pr-0
          "
        >
          <div class="font-halvar items-center flex">
            <div class="block items-center text-right mr-6">
              <div class="text-[#E7D8FF] text-sm">
                {{ language == "en" ? "BALANCE" : "残高" }}
              </div>
              <div class="text-[#9577D1] text-lg flex items-center justify-end font-halvar_bold">
                5000<svg
                  viewBox="0 0 16 16"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                  width="16"
                  height="16"
                  class="ml-1"
                  style="transform: rotate(0deg)"
                >
                  <path
                    data-v-0894134b=""
                    fill-rule="evenodd"
                    clip-rule="evenodd"
                    d="M8 2.828L2.83 8 8 13.17 13.172 8 8 2.828zM1.414 6.586a2 2 0 000 2.828l5.172 5.172a2 2 0 002.828 0l5.172-5.172a2 2 0 000-2.828L9.414 1.414a2 2 0 00-2.828 0L1.414 6.586z"
                    fill="currentColor"
                  ></path>
                </svg>
              </div>
            </div>
            <img class="" />
          </div>

          <!-- Profile dropdown -->
          <Menu as="div" class="ml-3 relative">
            <div>
              <MenuButton
                class="
                  bg-[#703ED9]
                  flex
                  text-sm
                  rounded-full
                  focus:outline-none
                  active:ring-2
                  focus:ring-offset-2
                  hover:ring-offset-gray-800
                  active:ring-[#703ED9]
                "
              >
                <span class="sr-only">Open user menu</span>
                <img
                  class="h-12 w-12 object-cover rounded-full"
                  src="https://c.tenor.com/dR6vK_dQ1UgAAAAC/%C3%B3culos-escuro.gif"
                  alt=""
                />
              </MenuButton>
            </div>
            <transition
              enter-active-class="transition ease-out duration-100"
              enter-from-class="transform opacity-0 scale-95"
              enter-to-class="transform opacity-100 scale-100"
              leave-active-class="transition ease-in duration-75"
              leave-from-class="transform opacity-100 scale-100"
              leave-to-class="transform opacity-0 scale-95"
            >
              <MenuItems
                class="
                  origin-top-right
                  absolute
                  right-0
                  z-1
                  mt-2
                  w-48
                  rounded-md
                  shadow-lg
                  py-1
                  text-[#9A8EAE]
                  bg-[#0F071F]
                  ring-1 ring-black ring-opacity-5
                  focus:outline-none
                "
              >
                <MenuItem v-slot="{ active }">
                  <NuxtLink
                    to="/settings"
                    :class="[
                      active ? 'bg-[#231739]' : '',
                      'block px-4 py-2 text-sm text-[#9A8EAE] flex items-center',
                    ]"
                    ><UserCircleIcon class="h-5 w-5 mr-1" />{{ language == 'en' ? 'Settings' : '口座'}}</NuxtLink
                  >
                </MenuItem>
                <MenuItem v-slot="{ active }">
                  <a
                    href="#"
                    :class="[
                      active ? 'bg-[#231739]' : '',
                      'block px-4 py-2 text-sm text-[#9A8EAE] flex items-center',
                    ]"
                    ><SparklesIcon class="h-5 w-5 mr-1" />{{ language == 'en' ? 'Upgrade' : '上り坂'}}</a
                  >
                </MenuItem>
                <MenuItem v-slot="{ active }">
                  <a
                    href="#"
                    :class="[
                      active ? 'bg-[#231739]' : '',
                      'block px-4 py-2 text-sm text-[#9A8EAE] flex items-center',
                    ]"
                    ><BellIcon class="h-5 w-5 mr-1" />{{ language == 'en' ? 'Tell a friend' : '照会'}}</a
                  >
                </MenuItem>
                <MenuItem v-slot="{ active }">
                  <a
                    href="#"
                    :class="[
                      active ? 'bg-[#231739]' : '',
                      'block px-4 py-2 text-sm text-[#9A8EAE] flex items-center',
                    ]"
                    ><LogoutIcon class="h-5 w-5 mr-1" />{{ language == 'en' ? 'Log out' : '離れる'}}</a
                  >
                </MenuItem>
              </MenuItems>
            </transition>
          </Menu>
        </div>
      </div>
    </div>

    <DisclosurePanel class="sm:hidden">
      <div class="px-2 pt-2 pb-3 space-y-1 flex items-center">
        <DisclosureButton
          v-for="item in navigation"
          :key="item.name"
          as="a"
          :href="item.href"
          :class="[
            active
              ? 'bg-gray-900 text-white'
              : 'text-gray-300 hover:bg-gray-700 hover:text-white',
            'block px-3 py-2 rounded-md text-base font-medium',
          ]"
          :aria-current="active ? 'page' : undefined"
          >{{ item.name }}</DisclosureButton
        >
      </div>
    </DisclosurePanel>
  </Disclosure>
</template>

<script setup>
import {
  Disclosure,
  DisclosureButton,
  DisclosurePanel,
  Menu,
  MenuButton,
  MenuItem,
  MenuItems,
} from "@headlessui/vue";
import {
  BellIcon,
  MenuIcon,
  XIcon,
  TranslateIcon,
} from "@heroicons/vue/outline";

import { SparklesIcon, LogoutIcon, UserCircleIcon } from "@heroicons/vue/solid";

const route = useRoute();
</script>

<script>
export default {
  data() {
    return {
      language: "en",
    };
  },
  computed: {
    navigation() {
      if (this.language === "en")
        return [
          { name: "Heroes", href: "/", current: false, icon: BellIcon },
          {
            name: "Actions",
            href: "/actions",
            current: false,
            icon: BellIcon,
          },
        ];
      else
        return [
          { name: "家", href: "/", current: false, icon: BellIcon },
          // {
          //   name: "市場",
          //   href: "/marketplace",
          //   current: false,
          //   icon: BellIcon,
          // },
        ];
    },
  },
  beforeMount() {
    this.language = localStorage.lang;
  },
  methods: {
    changeLang() {
      if (this.language === "ja") {
        this.language = "en";
        localStorage.lang = "en";
      } else {
        this.language = "ja";
        localStorage.lang = "ja";
      }
    },
  },
};
</script>


<style scoped>
</style>