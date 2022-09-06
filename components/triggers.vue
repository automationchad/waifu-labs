<template>
  <div class="px-4 sm:px-6 lg:px-8 py-6">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-xl font-semibold text-white">Triggers</h1>
        <p class="mt-2 text-sm text-gray-400">
          A list of all the triggers for your waifu.
        </p>
      </div>
      
    </div>
    <div class="mt-8 flex flex-col">
      <div class="-my-2 -mx-4 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle md:px-6 lg:px-8">
          <div
            class="
              overflow-hidden
              shadow
              ring-1 ring-black ring-opacity-5
              md:rounded-lg
            "
          >
            <table class="min-w-full ">
              <thead class="bg-[#1F1F23]">
                <tr class="text-white">
                  <th
                    scope="col"
                    class="
                      py-3.5
                      pl-4
                      pr-3
                      text-left text-sm
                      font-semibold
                      sm:pl-6
                    "
                  >
                    Command
                  </th>
                  <th
                    scope="col"
                    class="
                      px-3
                      py-3.5
                      text-left text-sm
                      font-semibold
                      
                    "
                  >
                    Message
                  </th>
                  <th
                    scope="col"
                    class="
                      px-3
                      py-3.5
                      text-left text-sm
                      font-semibold
                      
                    "
                  >
                    Action
                  </th>
                  <th
                    scope="col"
                    class="
                      px-3
                      py-3.5
                      text-left text-sm
                      font-semibold
                      
                    "
                  >
                    Status
                  </th>

                  <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-6">
                    <span class="sr-only">Edit</span>
                  </th>
                </tr>
              </thead>
              <tbody class="divide-y divide-[#1F1F23] bg-[#18191A]">
                <tr v-for="command in commands" :key="command.id" class="text-white">
                  <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm sm:pl-6">
                    <div class="flex items-center">
                      <!-- <div class="h-10 w-10 flex-shrink-0">
                        <img class="h-10 w-10 rounded-full" :src="person.image" alt="" />
                      </div> -->
                      <div class="ml-0">
                        <div class="font-medium ">
                          {{ command.name }}
                        </div>
                        <!-- <div class="text-gray-500">{{ command.type }}</div> -->
                      </div>
                    </div>
                  </td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
                    <div class="">{{ command.message }}</div>
                    <!-- <div class="text-gray-500">{{ person.department }}</div> -->
                  </td>

                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
                    {{ command.animation }}
                  </td>
                  <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
                    <Switch
                      @click="updateEnabled(command.id)"
                      :class="[
                        command.enabled ? 'bg-[#762CE9]' : 'bg-[#1F1F23]',
                        'relative inline-flex flex-shrink-0 h-6 w-11 border-2 border-transparent rounded-full cursor-pointer transition-colors ease-in-out duration-200 focus:outline-none',
                      ]"
                    >
                      <span class="sr-only">Use setting</span>
                      <span
                        :class="[
                          command.enabled ? 'translate-x-5' : 'translate-x-0',
                          'pointer-events-none relative inline-block h-5 w-5 rounded-full bg-white shadow transform ring-0 transition ease-in-out duration-200',
                        ]"
                      >
                        <span
                          :class="[
                            command.enabled
                              ? 'opacity-0 ease-out duration-100'
                              : 'opacity-100 ease-in duration-200',
                            'absolute inset-0 h-full w-full flex items-center justify-center transition-opacity',
                          ]"
                          aria-hidden="true"
                        >
                          <svg
                            class="h-3 w-3 text-gray-400"
                            fill="none"
                            viewBox="0 0 12 12"
                          >
                            <path
                              d="M4 8l2-2m0 0l2-2M6 6L4 4m2 2l2 2"
                              stroke="currentColor"
                              stroke-width="2"
                              stroke-linecap="round"
                              stroke-linejoin="round"
                            />
                          </svg>
                        </span>
                        <span
                          :class="[
                            command.enabled
                              ? 'opacity-100 ease-in duration-200'
                              : 'opacity-0 ease-out duration-100',
                            'absolute inset-0 h-full w-full flex items-center justify-center transition-opacity',
                          ]"
                          aria-hidden="true"
                        >
                          <svg
                            class="h-3 w-3 text-gray-400"
                            fill="currentColor"
                            viewBox="0 0 12 12"
                          >
                            <path
                              d="M3.707 5.293a1 1 0 00-1.414 1.414l1.414-1.414zM5 8l-.707.707a1 1 0 001.414 0L5 8zm4.707-3.293a1 1 0 00-1.414-1.414l1.414 1.414zm-7.414 2l2 2 1.414-1.414-2-2-1.414 1.414zm3.414 2l4-4-1.414-1.414-4 4 1.414 1.414z"
                            />
                          </svg>
                        </span>
                      </span>
                    </Switch>
                    <!-- <span
                          :class="[
                            command.enabled
                              ? 'text-green-800 bg-green-100'
                              : 'text-red-800 bg-red-100',
                            'inline-flex rounded-full  px-2 text-xs font-semibold leading-5 ',
                          ]"
                          >{{ command.enabled ? "Active" : "Disabled" }}</span
                        > -->
                  </td>
                  <td
                    class="
                      relative
                      whitespace-nowrap
                      py-4
                      pl-3
                      pr-4
                      text-right text-sm
                      font-medium
                      sm:pr-6
                    "
                  >
                    <NuxtLink
                      :to="this.$route.path + '/commands/' + command.id"
                      class="text-[#BF94FF] hover:text-[#785ca3]"
                      ><div class="flex justify-end">
                        <PencilAltIcon class="h-5 w-5 mr-1" />Edit<span
                          class="sr-only"
                          >, {{ command.id }}</span
                        >
                      </div></NuxtLink
                    >
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { Switch } from "@headlessui/vue";
import { PencilAltIcon } from "@heroicons/vue/solid";

const route = useRoute();
</script>

<script>
export default {
  data() {
    return {
      commands: [
        {
          name: "greet",
          message: "Hi, $username!",
          animation: "dance",
          type: "auto",
          enabled: true,
          id: 1,
        },
        {
          name: "sub",
          message: "Thanks for the sub, $username!",
          animation: "sexy",
          type: "trigger",
          enabled: false,
          id: 2,
        },
        {
          name: "resub",
          message: "Thanks for the resub, $username!",
          animation: "dance",
          type: "trigger",
          enabled: true,
          id: 3,
        },
      ],
    };
  },
  methods: {
    updateEnabled(value) {
      const index = this.commands.findIndex((o) => {
        return o.id === value;
      });
      this.commands[index].enabled = !this.commands[index].enabled;
    },
  },
};
</script>
