<template>
  <div class="px-4 sm:px-6 lg:px-8 py-6">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-xl font-semibold text-white">Rewards</h1>
        <p class="mt-2 text-sm text-gray-400">
          A list of all the rewards for your waifu.
        </p>
      </div>
      <div class="mt-4 sm:mt-0 sm:ml-16 sm:flex-none">
        <button
          v-if="people.length > 0"
          @click="open = true"
          type="button"
          class="
            inline-flex
            items-center
            justify-center
            rounded-md
            border border-transparent
            bg-indigo-600
            px-4
            py-2
            text-sm
            font-medium
            text-white
            shadow-sm
            hover:bg-indigo-700
            focus:outline-none
            focus:ring-2
            focus:ring-indigo-500
            focus:ring-offset-2
            sm:w-auto
          "
        >
          Add reward
        </button>
      </div>
    </div>
    <div v-if="people.length > 0" class="mt-8">
      <ul
        role="list"
        class="
          grid grid-cols-1
          gap-6
          sm:grid-cols-2
          md:grid-cols-3
          lg:grid-cols-4
        "
      >
        <li
          v-for="person in people"
          :key="person.email"
          class="
            col-span-1
            flex flex-col
            text-center
            bg-white
            rounded-lg
            shadow
            divide-y divide-gray-200
          "
        >
          <div class="flex-1 flex flex-col p-8">
            <img
              class="h-48 flex-shrink-0 mx-auto rounded"
              :src="person.imageUrl"
              alt=""
            />
            <h3 class="mt-6 text-gray-900 text-sm font-medium">
              {{ person.title }}
            </h3>
            <dl class="mt-1 flex-grow flex flex-col justify-between">
              <dt class="sr-only">Title</dt>
              <dd class="text-gray-500 text-sm">{{ person.prompt }}</dd>
              <dt class="sr-only">Role</dt>
              <dd class="mt-3 flex justify-center">
                <div
                  class="
                    px-2
                    py-1
                    text-green-800 text-xs
                    font-medium
                    bg-green-100
                    rounded-full
                    flex
                    items-center
                    justify-center
                  "
                >
                  {{ person.cost }}<CashIcon class="h-4 w-4 ml-1" />
                </div>
              </dd>
            </dl>
          </div>
          <div>
            <div class="-mt-px flex divide-x divide-gray-200">
              <div class="w-0 flex-1 flex">
                <button
                  @click="deleteReward(person.id)"
                  class="
                    relative
                    -mr-px
                    w-0
                    flex-1
                    inline-flex
                    items-center
                    justify-center
                    py-4
                    text-sm text-gray-700
                    font-medium
                    border border-transparent
                    rounded-bl-lg
                    hover:text-gray-500
                  "
                >
                  <TrashIcon class="w-5 h-5 text-gray-400" aria-hidden="true" />
                  <span class="ml-3">Delete</span>
                </button>
              </div>
              <div class="-ml-px w-0 flex-1 flex">
                <a
                  :href="`${this.$route.path}/rewards/${person.id}`"
                  class="
                    relative
                    w-0
                    flex-1
                    inline-flex
                    items-center
                    justify-center
                    py-4
                    text-sm text-gray-700
                    font-medium
                    border border-transparent
                    rounded-br-lg
                    hover:text-gray-500
                  "
                >
                  <PencilAltIcon
                    class="w-5 h-5 text-gray-400"
                    aria-hidden="true"
                  />
                  <span class="ml-3">Edit</span>
                </a>
              </div>
            </div>
          </div>
        </li>
      </ul>
    </div>
    <div
      v-else
      class="
        text-center
        mt-8
        p-12
        border-gray-300 border-dashed
        w-full
        border-2
        rounded-lg
      "
    >
      <svg
        class="mx-auto h-12 w-12 text-gray-400"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
        aria-hidden="true"
      >
        <path
          vector-effect="non-scaling-stroke"
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M9 13h6m-3-3v6m-9 1V7a2 2 0 012-2h6l2 2h6a2 2 0 012 2v8a2 2 0 01-2 2H5a2 2 0 01-2-2z"
        />
      </svg>
      <h3 class="mt-2 text-sm font-medium text-white">No rewards</h3>
      <p class="mt-1 text-sm text-gray-500">
        Get started by creating a new reward.
      </p>
      <div class="mt-6">
        <button
          @click="createNew()"
          type="button"
          class="
            inline-flex
            items-center
            px-4
            py-2
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
          <PlusIcon class="-ml-1 mr-2 h-5 w-5" aria-hidden="true" />
          New Reward
        </button>
      </div>
    </div>
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
            class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
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
                  bg-white
                  rounded-lg
                  px-4
                  pt-5
                  pb-4
                  text-left
                  overflow-hidden
                  shadow-xl
                  transform
                  transition-all
                  sm:my-8 sm:max-w-2xl sm:w-full sm:p-6
                "
              >
                <form class="space-y-8 divide-y divide-gray-200">
                  <div class="space-y-8 divide-gray-200">
                    <div>
                      <!-- <div>
              <h3 class="text-lg leading-6 font-medium text-white">Profile</h3>
              <p class="mt-1 text-sm text-gray-500">
                This information will be displayed publicly so be careful what
                you share.
              </p>
            </div> -->

                      <div
                        class="grid grid-cols-1 gap-y-6 gap-x-4 sm:grid-cols-6"
                      >
                        <div class="col-span-4">
                          <label
                            for="email"
                            class="block text-sm font-medium text-black"
                            >Title</label
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
                                  class="h-5 w-5 text-gray-400"
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
                                  border-gray-300
                                "
                                v-on:focus="$event.target.select()"
                                ref="clone"
                                placeholder="greet"
                                required
                              />
                            </div>
                          </div>
                        </div>

                        <div class="col-span-2">
                          <div>
                            <label
                              for="account-number"
                              class="block text-sm font-medium text-gray-700"
                              >Cost</label
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
                                  border-gray-300
                                  rounded-md
                                "
                                placeholder="0"
                                required
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
                                <CashIcon
                                  class="h-5 w-5 text-gray-400"
                                  aria-hidden="true"
                                />
                              </div>
                            </div>
                          </div>
                        </div>
                        <div class="col-span-6">
                          <div class="flex justify-between">
                            <label
                              for="email"
                              class="block text-sm font-medium text-gray-700"
                              >Prompt</label
                            >
                            <span
                              class="text-sm text-gray-500"
                              id="email-optional"
                              >Optional</span
                            >
                          </div>
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
                              placeholder="The prompt for the viewer when redeeming the reward."
                              aria-describedby="email-optional"
                            />
                          </div>
                        </div>

                        <div class="sm:col-span-6">
                          <div class="flex justify-between">
                            <label
                              for="about"
                              class="block text-sm font-medium text-gray-700"
                              >Message</label
                            >
                            <span
                              class="text-sm text-gray-500"
                              id="email-optional"
                              >Optional</span
                            >
                          </div>
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
                              placeholder="The text you want your waifu to say upon reward redemption"
                            />
                          </div>
                          <p class="mt-2 text-sm text-gray-500">
                            Allowed variables: $username, $monthcount,
                            $bitcount, $recipient
                          </p>
                        </div>

                        <div class="sm:col-span-6">
                          <label
                            for="photo"
                            class="block text-sm font-medium text-gray-700"
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
                                class="
                                  flex
                                  items-center
                                  justify-center
                                  space-x-1
                                  h-auto
                                "
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
                                        class="
                                          ml-3
                                          block
                                          text-sm
                                          font-medium
                                          text-white
                                        "
                                      >
                                        {{ outfit.name }}
                                      </label>
                                    </div>
                                  </div>
                                </div>
                                <!-- <div
                        v-for="outfit in outfits"
                        :key="outfit.id"
                        class="
                          flex flex-col
                          justify-center
                          items-center
                          h-72
                          w-36
                        "
                      >
                        <button
                          :class="[
                            defaultOutfit === outfit.id
                              ? 'border-white border-y-2'
                              : '',
                            'h-full w-full  bg-white/50 bg-cover bg-center',
                          ]"
                          :style="{ 'background-image': outfit.src }"
                          @click="setDefault(outfit.id)"
                          :disabled="!outfit.unlocked"
                        >
                          <div
                            :class="[
                              outfit.unlocked
                                ? 'hover:bg-white/20 cursor-pointer'
                                : 'bg-black/70',
                              'h-full w-full transition-colors',
                            ]"
                          >
                            <div class="items-end justify-end flex p-2">
                              <LockClosedIcon
                                v-if="!outfit.unlocked"
                                class="h-4 w-4 text-gray-500"
                              />
                            </div>
                          </div>
                        </button>
                        <a class=""
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
                        </div>
                      </div>
                    </div>
                  </div>

                  <div class="pt-5">
                    <div class="flex justify-end">
                      <button
                        @click="open = false"
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
                        Cancel
                      </button>
                      <button
                        @click="saveNew()"
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
  Switch,
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import {
  PencilAltIcon,
  TrashIcon,
  CashIcon,
  ExclamationIcon,
  XIcon,
  PlusIcon,
  ChatAltIcon,
} from "@heroicons/vue/solid";

const route = useRoute();
</script>

<script>
export default {
  data() {
    return {
      open: ref(false),
      showSave: ref(false),
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
          name: "Dance 1",
          unlocked: true,
          cost: 10000,
          id: "dance_1",
          src: "url(https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9c/Anna_Wealth-Wisher_Face.webp?version=596c36b8c62ae3f6ecc43535ee280b84)",
        },
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
      
      people: [
        {
          title: "Make her dance",
          id: "8hytegjkLo3",
          cost: 500,
          prompt: "Makes her dance",
          imageUrl:
            "https://gamepedia.cursecdn.com/feheroes_gamepedia_en/9/9c/Anna_Wealth-Wisher_Face.webp?version=596c36b8c62ae3f6ecc43535ee280b84",
        },
        // More people...
      ],
    };
  },
  methods: {
    createNew() {
      this.open = true;
    },
    saveNew() {
      setTimeout((this.showSave = true), 5000);
    },
    updateEnabled(value) {
      const index = this.commands.findIndex((o) => o.id === value);
      this.commands[index].enabled = !this.commands[index].enabled;
    },
    deleteReward(value) {
      const index = this.people.findIndex((o) => o.id === value);
      if (index > -1) {
        this.people.splice(index, 1);
      }
    },
  },
};
</script>
