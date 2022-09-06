<template>
  <div
    class="h-screen bg-cover bg-no-repeat flex bg-[#0F0F10]"
    
  >
    <div class="max-w-3xl max-auto pb-10 lg:py-12 lg:px-8 pt-6 ">
      <form
        class="
          space-y-8
          divide-y divide-gray-200
          bg-[#18191A]
          backdrop-blur-md
          rounded-xl
          p-12
        "
      >
        <div class="space-y-8 divide-gray-200">
          <div>
            <!-- <div>
              <h3 class="text-lg leading-6 font-medium text-white">Profile</h3>
              <p class="mt-1 text-sm text-gray-500">
                This information will be displayed publicly so be careful what
                you share.
              </p>
            </div> -->

            <div class="grid grid-cols-1 gap-y-6 gap-x-4 sm:grid-cols-6">
              <div class="col-span-2">
                <label
                  for="email"
                  class="block text-sm font-medium text-white"
                  >Trigger</label
                >
                <div class="mt-1 flex rounded-md shadow-sm">
                  <div
                    class="
                      relative
                      flex
                      items-stretch
                      flex-grow
                      focus-within:z-10
                    "
                  >
                    <div
                      class="
                        absolute
                        inset-y-0
                        left-0
                        pl-3
                        flex
                        items-center
                        pointer-events-none
                      "
                    >
                      <ChatAltIcon
                        class="h-5 w-5 text-gray-400"
                        aria-hidden="true"
                      />
                    </div>
                    <input
                      type="email"
                      name="email"
                      id="email"
                      class="
                        focus:ring-indigo-500 focus:border-indigo-500
                        block
                        text-gray-400
                        w-full
                        rounded-md
                        pl-10
                        sm:text-sm
                        border-gray-300
                      "
                      readonly
                      disabled
                      v-on:focus="$event.target.select()"
                      ref="clone"
                      placeholder="greet"
                    />
                  </div>
                </div>
              </div>

              <!-- <div class="col-span-2">
                <Listbox as="div" v-model="selected">
                  <ListboxLabel class="block text-sm font-medium text-gray-700">
                    Type
                  </ListboxLabel>
                  <div class="mt-1 relative">
                    <ListboxButton
                      class="
                        relative
                        w-full
                        bg-white
                        border border-gray-300
                        rounded-md
                        shadow-sm
                        pl-3
                        pr-10
                        py-2
                        text-left
                        cursor-default
                        focus:outline-none
                        focus:ring-1
                        focus:ring-indigo-500
                        focus:border-indigo-500
                        sm:text-sm
                      "
                    >
                      <span class="block truncate">{{ selected.name }}</span>
                      <span
                        class="
                          absolute
                          inset-y-0
                          right-0
                          flex
                          items-center
                          pr-2
                          pointer-events-none
                        "
                      >
                        <SelectorIcon
                          class="h-5 w-5 text-gray-400"
                          aria-hidden="true"
                        />
                      </span>
                    </ListboxButton>

                    <transition
                      leave-active-class="transition ease-in duration-100"
                      leave-from-class="opacity-100"
                      leave-to-class="opacity-0"
                    >
                      <ListboxOptions
                        class="
                          absolute
                          z-10
                          mt-1
                          w-full
                          bg-white
                          shadow-lg
                          max-h-60
                          rounded-md
                          py-1
                          text-base
                          ring-1 ring-black ring-opacity-5
                          overflow-auto
                          focus:outline-none
                          sm:text-sm
                        "
                      >
                        <ListboxOption
                          as="template"
                          v-for="type in types"
                          :key="type.id"
                          :value="type"
                          v-slot="{ active, selected }"
                        >
                          <li
                            :class="[
                              active
                                ? 'text-white bg-indigo-600'
                                : 'text-gray-900',
                              'cursor-default select-none relative py-2 pl-8 pr-4',
                            ]"
                          >
                            <span
                              :class="[
                                selected ? 'font-semibold' : 'font-normal',
                                'block truncate',
                              ]"
                            >
                              {{ type.name }}
                            </span>

                            <span
                              v-if="selected"
                              :class="[
                                active ? 'text-white' : 'text-indigo-600',
                                'absolute inset-y-0 left-0 flex items-center pl-1.5',
                              ]"
                            >
                              <CheckIcon class="h-5 w-5" aria-hidden="true" />
                            </span>
                          </li>
                        </ListboxOption>
                      </ListboxOptions>
                    </transition>
                  </div>
                </Listbox>
              </div> -->
              <div class="col-span-2">
                <div>
                  <label
                    for="location"
                    class="block text-sm font-medium text-white"
                    >User Group</label
                  >
                  <select
                    id="location"
                    name="location"
                    class="
                      mt-1
                      block
                      w-full
                      pl-3
                      pr-10
                      py-2
                      text-base
                      border-gray-300
                      focus:outline-none
                      focus:ring-indigo-500
                      focus:border-indigo-500
                      sm:text-sm
                      rounded-md
                    "
                  >
                    <option>Everyone</option>
                    <option selected="">Mods</option>
                    <option>Subs</option>
                    <option>Channel Owner</option>
                  </select>
                </div>
              </div>
              <div class="sm:col-span-6">
                <label
                  for="photo"
                  class="block text-sm font-medium text-white"
                >
                  Animation
                </label>
                <div class="mt-1 flex items-center">
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
                      class="flex items-center justify-center space-x-1 h-auto"
                    >
                      <div
                        v-for="outfit in outfits"
                        :key="outfit.id"
                        class="flex h-72 w-36 bg-cover bg-center"
                        :style="{ 'background-image': outfit.src }"
                      >
                        <div
                          :class="[
                            'h-full w-full transition-colors flex bg-black/20 items-end hover:bg-white/5',
                          ]"
                        >
                          <div
                            class="
                              backdrop-blur-md
                              bg-black/40
                              flex
                              w-full
                              p-2
                              items-center
                            "
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
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <!-- <div :class="[chatEnabled ? '' : 'opacity-50', 'sm:col-span-6']">
                <div>
                  <label
                    for="email"
                    class="block text-sm font-medium text-gray-700"
                    >Chat Alert</label
                  >
                  <div class="mt-1">
                    <input
                      type="email"
                      name="email"
                      id="email"
                      class="
                        shadow-sm
                        focus:ring-indigo-500 focus:border-indigo-500
                        block
                        w-full
                        sm:text-sm
                        border-gray-300
                        rounded-md
                      "
                      placeholder="#user sent a #gesture GESTURE FOR #bits"
                      aria-describedby="email-description"
                      :disabled="!chatEnabled"
                      :value="chatEnabled ? 'value' : ''"
                    />
                  </div>
                  <p class="mt-2 text-sm text-gray-500">
                    Customize the alert message to be posted in the chat room.
                    You can use the following tags:
                    <span class="text-purple-500 font-bold">#user</span> =
                    viewer name,
                    <span class="text-purple-500 font-bold">#gesture</span> =
                    gesture name
                  </p>
                </div>
              </div> -->
              <!-- <div
                :class="[overlayEnabled ? '' : 'opacity-50', 'sm:col-span-6']"
              >
                <label
                  for="about"
                  class="block text-sm font-medium text-gray-700"
                >
                  Overlay Alert
                </label>
                <div class="mt-1">
                  <textarea
                    id="about"
                    name="about"
                    rows="3"
                    class="
                      shadow-sm
                      focus:ring-indigo-500 focus:border-indigo-500
                      block
                      w-full
                      sm:text-sm
                      border border-gray-300
                      rounded-md
                    "
                    placeholder="#user sent a #gesture GESTURE FOR #bits"
                    :disabled="!overlayEnabled"
                    :value="overlayEnabled ? 'value' : ''"
                  />
                </div>
                <p class="mt-2 text-sm text-gray-500">
                  Customize the text message to be posted in the live stream. You
                  can use the following tags:
                  <span class="text-purple-500 font-bold">#user</span> = viewer
                  name,
                  <span class="text-purple-500 font-bold">#gesture</span> =
                  gesture name
                </p>
              </div> -->
            </div>
          </div>
        </div>

        <div class="pt-5">
          <div class="flex justify-end">
            <button
              type="button"
              class="
                bg-white
                py-2
                px-4
                border border-gray-300
                rounded-md
                shadow-sm
                text-sm
                font-medium
                text-gray-700
                hover:bg-gray-50
                focus:outline-none
                focus:ring-2
                focus:ring-offset-2
                focus:ring-indigo-500
              "
            >
              Disable
            </button>
            <button
              type="submit"
              class="
                ml-3
                inline-flex
                justify-center
                py-2
                px-4
                border border-transparent
                shadow-sm
                text-sm
                font-medium
                rounded-md
                text-white
                bg-indigo-600
                hover:bg-indigo-700
                focus:outline-none
                focus:ring-2
                focus:ring-offset-2
                focus:ring-indigo-500
              "
            >
              Save and enable
            </button>
          </div>
        </div>
      </form>
    </div>
    <div class="max-w-3xl mx-auto pb-10 lg:py-12 lg:px-8 pt-6">
      <div
        class="
          divide-gray-200
          rounded-xl
          p-8
          border-dashed border-white/50 border-2
        "
      >
        <div class="text-xl text-white/60 justify-between flex">
          <NuxtLink
            to="../"
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
            <ColorSwatchIcon class="h-5 w-5 mr-1" />
            Edit waifu
          </NuxtLink>
          <div>Preview</div>
        </div>
        <img
          class="max-h-[700px]"
          src="https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9e/Azura_Lady_of_the_Lake_Face.webp?version=c71d015ced79cac659d7b4bd5d2baf31"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ChatAltIcon } from "@heroicons/vue/solid";
import { ref } from "vue";
import {
  Listbox,
  ListboxButton,
  ListboxLabel,
  ListboxOption,
  ListboxOptions,
} from "@headlessui/vue";
import { CheckIcon, SelectorIcon, ColorSwatchIcon } from "@heroicons/vue/solid";

const types = [
  { id: 1, name: "Auto" },
  { id: 2, name: "Trigger" },
  { id: 3, name: "Keyword" },
  { id: 4, name: "Scheduled" },
];

const selected = ref(types[3]);
</script>

<script>
export default {
  data() {
    return {
      show: ref(false),
      overlayEnabled: Math.random() > 0.5,
      chatEnabled: Math.random() > 0.5,
      defaultOutfit: "outfit_2",
      outfits: [
        {
          name: "Dance 1",
          unlocked: true,
          cost: 10000,
          id: "dance_1",
          src: "url(https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9c/Anna_Wealth-Wisher_Face.webp?version=596c36b8c62ae3f6ecc43535ee280b84)",
        },
        {
          name: "Dance 2",
          unlocked: true,
          cost: 2000,
          id: "dance_2",
          src: "url(https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9e/Azura_Lady_of_the_Lake_Face.webp?version=c71d015ced79cac659d7b4bd5d2baf31)",
        },
        {
          name: "Dance 3",
          unlocked: true,
          cost: 100000,
          id: "dance_3",
          src: "url(https://cdn.wallpapersafari.com/30/33/fIpGAw.jpg)",
        },
      ],
    };
  },
  methods: {
    setDefault(value) {
      this.defaultOutfit = value;
    },
    savePreferences() {
      this.show = true;
      setTimeout(() => {
        this.show = false;
      }, 3000);
    },
  },
};
</script>