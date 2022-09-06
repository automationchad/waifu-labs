

<template>
  <div class="h-screen bg-cover bg-no-repeat flex bg-[#0F0F10]">
    <div class="max-w-3xl max-auto pb-10 lg:py-12 lg:px-8 pt-6">
      <form
        class="
          space-y-8
          divide-y divide-gray-200/10
          bg-[#18191A]
          backdrop-blur-md
          rounded-xl
          p-12
        "
      >
        <div class="space-y-8 divide-gray-200/10">
          <div>
            <div class="grid grid-cols-1 gap-y-6 gap-x-4 sm:grid-cols-6">
              <div class="col-span-4">
                <label for="email" class="block text-sm font-medium text-white"
                  >Gesture</label
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
                        text-black
                      "
                    >
                      <ChatAltIcon
                        class="h-5 w-5 text-white"
                        aria-hidden="true"
                      />
                    </div>
                    <input
                      type="text"
                      name="email"
                      id="title"
                      class="
                        focus:ring-indigo-500 focus:border-indigo-500
                        block
                        w-full
                        rounded-md
                        pl-10
                        sm:text-sm
                        border-gray-300/10
                        bg-white/10
                        text-white
                      "
                      v-on:focus="$event.target.select()"
                      ref="clone"
                      disabled
                      value="The Floss"
                    />
                  </div>
                </div>
              </div>
              <div class="col-span-2">
                <div>
                  <label
                    for="account-number"
                    class="block text-sm font-medium text-white"
                    >Bit Threshold</label
                  >
                  <div class="mt-1 relative rounded-md shadow-sm">
                    <input
                      type="text"
                      name="account-number"
                      id="account-number"
                      class="
                        focus:ring-indigo-500 focus:border-indigo-500
                        block
                        w-full
                        pr-10
                        sm:text-sm
                        border-gray-300/10
                        bg-white/10
                        rounded-md
                        text-white
                      "
                      placeholder="0"
                      value="500"
                    />
                    <div
                      class="
                        absolute
                        inset-y-0
                        right-0
                        pr-3
                        flex
                        items-center
                        pointer-events-none
                      "
                    >
                      <svg
                        class="h-4 text-gray-400"
                        version="1.1"
                        viewBox="0 0 20 20"
                        x="0px"
                        y="0px"
                        fill="currentColor"
                      >
                        <path
                          fill-rule="evenodd"
                          clip-rule="evenodd"
                          d="M3 12l7-10 7 10-7 6-7-6zm2.678-.338L10 5.487l4.322 6.173-.85.728L10 11l-3.473 1.39-.849-.729z"
                        ></path>
                      </svg>
                    </div>
                  </div>
                </div>
              </div>
              <!-- <div class="sm:col-span-6">
                <label
                  for="photo"
                  class="block text-sm font-medium text-gray-700"
                >
                  Gesture
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
              </div> -->
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
                    gesture name,
                    <span class="text-purple-500 font-bold">#bits</span> =
                    amount of Bits used
                  </p>
                </div>
              </div>
              <div
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
                  Customize the text message to be posted in the live stream.
                  You can use the following tags:
                  <span class="text-purple-500 font-bold">#user</span> = viewer
                  name,
                  <span class="text-purple-500 font-bold">#gesture</span> =
                  gesture name,
                  <span class="text-purple-500 font-bold">#bits</span> = amount
                  of Bits used
                </p>
              </div> -->
            </div>
          </div>
        </div>

        <div class="pt-5">
          <div class="flex justify-end">
            <button
              @click="$router.go(-1)"
              type="button"
              class="
                bg-[#474749]
                py-2
                px-4
                border border-gray-300/10
                rounded-md
                shadow-sm
                text-sm
                font-medium
                text-white
                hover:bg-gray-50/10
                focus:outline-none
                focus:ring-2
                focus:ring-offset-2
                focus:ring-indigo-500
              "
            >
              Cancel
            </button>
            <button
              @click="savePreferences()"
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
                bg-[#9047FF]
                hover:bg-indigo-700
                focus:outline-none
                focus:ring-2
                focus:ring-offset-2
                focus:ring-indigo-500
              "
            >
              Save
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
            to="/"
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
    <div
      aria-live="assertive"
      class="
        fixed
        inset-0
        top-20
        flex
        items-end
        px-4
        py-6
        pointer-events-none
        sm:p-6 sm:items-start
      "
    >
      <div class="w-full flex flex-col items-center space-y-4 sm:items-end">
        <!-- Notification panel, dynamically insert this into the live region when it needs to be displayed -->
        <transition
          enter-active-class="transform ease-out duration-300 transition"
          enter-from-class="translate-y-2 opacity-0 sm:translate-y-0 sm:translate-x-2"
          enter-to-class="translate-y-0 opacity-100 sm:translate-x-0"
          leave-active-class="transition ease-in duration-100"
          leave-from-class="opacity-100"
          leave-to-class="opacity-0"
        >
          <div
            v-if="showSave"
            class="
              max-w-sm
              w-full
              bg-white
              shadow-lg
              rounded-lg
              pointer-events-auto
              ring-1 ring-black ring-opacity-5
              overflow-hidden
            "
          >
            <div class="p-4">
              <div class="flex items-start">
                <div class="flex-shrink-0">
                  <CheckCircleIcon
                    class="h-6 w-6 text-green-400"
                    aria-hidden="true"
                  />
                </div>
                <div class="ml-3 w-0 flex-1 pt-0.5">
                  <p class="text-sm font-medium text-gray-900">
                    Successfully saved!
                  </p>
                  <p class="mt-1 text-sm text-gray-500">
                    Anyone with a link can now view this file.
                  </p>
                </div>
                <div class="ml-4 flex-shrink-0 flex">
                  <button
                    type="button"
                    @click="show = false"
                    class="
                      bg-white
                      rounded-md
                      inline-flex
                      text-gray-400
                      hover:text-gray-500
                      focus:outline-none
                      focus:ring-2
                      focus:ring-offset-2
                      focus:ring-indigo-500
                    "
                  >
                    <span class="sr-only">Close</span>
                    <XIcon class="h-5 w-5" aria-hidden="true" />
                  </button>
                </div>
              </div>
            </div>
          </div>
        </transition>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import {
  Listbox,
  ListboxButton,
  ListboxLabel,
  ListboxOption,
  ListboxOptions,
} from "@headlessui/vue";
import {
  CheckIcon,
  CheckCircleIcon,
  SelectorIcon,
  ColorSwatchIcon,
  ChatAltIcon,
  CashIcon,
} from "@heroicons/vue/solid";

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
      show: ref(true),
      showSave: ref(false),
      overlayEnabled: false,
      chatEnabled: false,
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
      this.showSave = true;
      setTimeout(() => {
        this.showSave = false;
      }, 3000);
    },
  },
};
</script>