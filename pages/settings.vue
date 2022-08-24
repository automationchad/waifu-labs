<template>
  <div class="h-full bg-black">
    <main class="max-w-7xl mx-auto pb-10 lg:py-12 lg:px-8">
      <div class="lg:grid lg:grid-cols-12 lg:gap-x-5">
        <aside class="py-6 px-2 sm:px-6 lg:py-0 lg:px-0 lg:col-span-3">
          <nav class="space-y-1">
            <a
              v-for="item in subNavigation"
              :key="item.name"
              @click="changeTab(item.id)"
              :href="item.href"
              :class="[
                tab === item.id
                  ? 'bg-[#231739] text-[#9A8EAE]'
                  : 'text-[#9A8EAE] hover:text-[#9A8EAE] hover:bg-[#0F071F]',
                'group rounded-md px-3 py-2 flex items-center text-sm font-medium',
              ]"
              :aria-current="tab === item.id ? 'page' : undefined"
            >
              <component
                :is="item.icon"
                :class="[
                  tab === item.id
                    ? 'text-[#9A8EAE]'
                    : 'text-[#9A8EAE] group-hover:text-[#9A8EAE]',
                  'flex-shrink-0 -ml-1 mr-3 h-6 w-6',
                ]"
                aria-hidden="true"
              />
              <span class="truncate">
                {{ item.name }}
              </span>
            </a>
          </nav>
        </aside>

        <!-- Payment details -->
        <paymentSettings v-if="tab === 'billing'" />
        <profileSettings v-else-if="tab === 'account'" />
        <notificationSettings v-else-if="tab === 'notifications'" />
        <integrationSettings v-else />
      </div>
    </main>
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
  RadioGroup,
  RadioGroupDescription,
  RadioGroupLabel,
  RadioGroupOption,
  Switch,
  SwitchGroup,
  SwitchLabel,
} from "@headlessui/vue";
import { QuestionMarkCircleIcon, SearchIcon } from "@heroicons/vue/solid";
import {
  BellIcon,
  CogIcon,
  CreditCardIcon,
  KeyIcon,
  MenuIcon,
  UserCircleIcon,
  ViewGridAddIcon,
  XIcon,
} from "@heroicons/vue/outline";

// const user = {
//   name: 'Lisa Marie',
//   email: 'lisamarie@example.com',
//   imageUrl:
//     'https://images.unsplash.com/photo-1517365830460-955ce3ccd263?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=4&w=256&h=256&q=80',
// }

const subNavigation = [
  //   { name: 'Profile', href: '#', icon: UserCircleIcon, current: false },
  { name: "Account", href: "#", id: "account", icon: CogIcon, current: false },
  //   { name: 'Password', href: '#', icon: KeyIcon, current: false },
    { name: 'Notifications', href: '#', id: 'notifications', icon: BellIcon, current: false },
  {
    name: "Plan & Billing",
    href: "#",
    id: "billing",
    icon: CreditCardIcon,
    current: true,
  },
    { name: 'Integrations', href: '#', id: 'integrations', icon: ViewGridAddIcon, current: false },
];
</script>

<script>
export default {
  data() {
    return {
      tab: "account",
    };
  },
  methods: {
    changeTab(value) {
      this.tab = value;
    },
  },
};
</script>