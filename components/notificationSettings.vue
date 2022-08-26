<template>
  <div class="space-y-6 sm:px-6 lg:px-0 lg:col-span-9">
    <form action="#" method="POST">
      <div class="shadow sm:rounded-md sm:overflow-hidden">
        <div class="bg-white py-6 px-4 space-y-6 sm:p-6">
          <div>
            <h3 class="text-lg leading-6 font-medium text-gray-900">Alerts</h3>
            <p class="mt-1 text-sm text-gray-500">
              We'll always trigger gestures, but you pick what else you want displayed.
            </p>
          </div>
          <SwitchGroup as="div" class="flex items-center justify-between">
            <span class="flex-grow flex flex-col">
              <SwitchLabel
                as="span"
                class="text-sm font-medium text-gray-900"
                passive
                >Overlay Alert</SwitchLabel
              >
              <SwitchDescription as="span" class="text-sm text-gray-500">
                This feature displays a customized text message on the live
                stream when a viewer sends a cheer.</SwitchDescription
              >
            </span>
            <Switch
              v-model="enabled"
              :class="[
                enabled ? 'bg-indigo-600' : 'bg-gray-200',
                'relative inline-flex flex-shrink-0 h-6 w-11 border-2 border-transparent rounded-full cursor-pointer transition-colors ease-in-out duration-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500',
              ]"
            >
              <span
                aria-hidden="true"
                :class="[
                  enabled ? 'translate-x-5' : 'translate-x-0',
                  'pointer-events-none inline-block h-5 w-5 rounded-full bg-white shadow transform ring-0 transition ease-in-out duration-200',
                ]"
              />
            </Switch>
          </SwitchGroup>
          <SwitchGroup as="div" class="flex items-center justify-between">
            <span class="flex-grow flex flex-col">
              <SwitchLabel
                as="span"
                class="text-sm font-medium text-gray-900"
                passive
                >Chat Alert</SwitchLabel
              >
              <SwitchDescription as="span" class="text-sm text-gray-500"
                >Displays a text alert message in the chat room when a viewer
                cheers with bits.</SwitchDescription
              >
            </span>
            <Switch
              v-model="enabled"
              :class="[
                enabled ? 'bg-indigo-600' : 'bg-gray-200',
                'relative inline-flex flex-shrink-0 h-6 w-11 border-2 border-transparent rounded-full cursor-pointer transition-colors ease-in-out duration-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500',
              ]"
            >
              <span
                aria-hidden="true"
                :class="[
                  enabled ? 'translate-x-5' : 'translate-x-0',
                  'pointer-events-none inline-block h-5 w-5 rounded-full bg-white shadow transform ring-0 transition ease-in-out duration-200',
                ]"
              />
            </Switch>
          </SwitchGroup>
          <div class="rounded-md bg-yellow-50 p-4">
            <div class="flex">
              <div class="flex-shrink-0">
                <ExclamationIcon
                  class="h-5 w-5 text-yellow-400"
                  aria-hidden="true"
                />
              </div>
              <div class="ml-3">
                <h3 class="text-sm font-medium text-yellow-800">
                  Important note
                </h3>
                <div class="mt-2 text-sm text-yellow-700">
                  <p>
                    Please be sure to give Waifulabs moderator status 
                    <a
                    class="font-bold underline"
                      id="chat-bot-roles-link"
                      target="_blank"
                      href="https://dashboard.twitch.tv/u/sevirance/community/roles"
                      >here</a
                    >
                    or by typing <span
                      id="chat-bot-mod-command"
                      class="bg-yellow-700 text-yellow-400 px-2 py-0.5 rounded"
                      
                      >/mod streamstickers</span
                    >
                     in your chat to prevent messages from being blocked
                    due to spam or follower-only mode filters, etc.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="px-4 py-3 bg-gray-50 text-right sm:px-6">
          <button
            type="submit"
            class="
              bg-indigo-600
              border border-transparent
              rounded-md
              shadow-sm
              py-2
              px-4
              inline-flex
              justify-center
              text-sm
              font-medium
              text-white
              hover:bg-indigo-700
              focus:outline-none
              focus:ring-2
              focus:ring-offset-2
              focus:ring-indigo-600
            "
          >
            Save
          </button>
        </div>
      </div>
    </form>
  </div>
</template>

<script setup>
import {
  CreditCardIcon,
  KeyIcon,
  UserCircleIcon,
  UserGroupIcon,
  ViewGridAddIcon,
  LinkIcon,
  ClipboardCopyIcon,
  ClipboardCheckIcon,
  ExclamationIcon,
} from "@heroicons/vue/outline";

import { ref } from "vue";
import {
  Switch,
  SwitchDescription,
  SwitchGroup,
  SwitchLabel,
} from "@headlessui/vue";

const enabled = ref(false);

const navigation = [
  { name: "Account", href: "#", icon: UserCircleIcon, current: true },
  { name: "Password", href: "#", icon: KeyIcon, current: false },
  { name: "Plan & Billing", href: "#", icon: CreditCardIcon, current: false },
  { name: "Team", href: "#", icon: UserGroupIcon, current: false },
  { name: "Integrations", href: "#", icon: ViewGridAddIcon, current: false },
];
</script>

<script>
export default {
  data() {
    return {
      copyValue: "Copy",
      streamURL:
        "https://stream.kappamon.com/t/2d081ff2-997a-4924-ae26-6c019e1cfb2b",
    };
  },
  methods: {
    copyButton() {
      this.$refs.clone.focus();
      document.execCommand("copy");
      this.copyValue = "Copied!";
      setTimeout(() => {
        this.copyValue = "Copy";
      }, 3000);
    },
  },
};
</script>