<template>
  <div class="space-y-6 sm:px-6 lg:px-0 lg:col-span-9">
    <form action="#" method="POST">
      <div class="shadow sm:rounded-md sm:overflow-hidden">
        <div class="bg-white py-6 px-4 space-y-6 sm:p-6">
          <div>
            <h3 class="text-lg leading-6 font-medium text-gray-900">Profile</h3>
            <p class="mt-1 text-sm text-gray-500">
              Configure this extension before you go live to provide the best experience for your viewers.
            </p>
          </div>

          <div class="grid grid-cols-3 gap-6">
            <div class="col-span-2">
              <label for="email" class="block text-sm font-medium text-gray-700"
                >Stream URL</label
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
                    <LinkIcon
                      class="h-5 w-5 text-gray-400 "
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
                      rounded-none rounded-l-md
                      pl-10
                      sm:text-sm
                      border-gray-300
                    "
                    :value="streamURL"
                    readonly
                    v-on:focus="$event.target.select()"
                    ref="clone"
                    placeholder="John Smith"
                  />
                </div>
                <button
                  type="button"
                  @click="copyButton()"
                  :disabled="copyValue !== 'Copy'"
                  class="
                    -ml-px
                    relative
                    inline-flex
                    items-center
                    space-x-2
                    px-4
                    py-2
                    border border-gray-300
                    text-sm
                    font-medium
                    rounded-r-md
                    text-gray-700
                    bg-gray-50
                    hover:bg-gray-100
                    disabled:bg-gray-50
                    focus:outline-none
                    focus:ring-1
                    focus:ring-indigo-500
                    focus:border-indigo-500
                  "
                >
                  <ClipboardCopyIcon v-if="copyValue === 'Copy'"
                    class="h-5 w-5 text-gray-400"
                    aria-hidden="true"
                  />
                  <ClipboardCheckIcon v-else
                    class="h-5 w-5 text-gray-400"
                    aria-hidden="true"
                  />
                  <span>{{ copyValue }}</span>
                </button>
              </div>
            </div>
            <!-- <div class="col-span-3 sm:col-span-2">
              <label
                for="company-website"
                class="block text-sm font-medium text-gray-700"
              >
                Username
              </label>
              <div class="mt-1 rounded-md shadow-sm flex">
                <span
                  class="
                    bg-gray-50
                    border border-r-0 border-gray-300
                    rounded-l-md
                    px-3
                    inline-flex
                    items-center
                    text-gray-500
                    sm:text-sm
                  "
                >
                  waifulabs.app/
                </span>
                <input
                  type="text"
                  name="username"
                  id="username"
                  value="sevirance"
                  autocomplete="username"
                  class="
                    focus:ring-indigo-500 focus:border-indigo-500
                    flex-grow
                    block
                    w-full
                    min-w-0
                    rounded-none rounded-r-md
                    sm:text-sm
                    border-gray-300
                  "
                />
              </div>
            </div> -->
            <div class="col-span-2 sm:col-span-2">
              <label
                for="email-address"
                class="block text-sm font-medium text-gray-700"
                >Email address</label
              >
              <input
                type="email"
                name="email-address"
                id="email-address"
                value="will@sevirance.com"
                autocomplete="email"
                class="
                  mt-1
                  block
                  w-full
                  border border-gray-300
                  rounded-md
                  shadow-sm
                  py-2
                  px-3
                  focus:outline-none
                  focus:ring-indigo-500
                  focus:border-indigo-500
                  sm:text-sm
                "
              />
            </div>
            <!-- <div class="col-span-3">
              <label
                for="about"
                class="block text-sm font-medium text-gray-700"
              >
                About
              </label>
              <div class="mt-1">
                <textarea
                  id="about"
                  name="about"
                  rows="3"
                  class="
                    shadow-sm
                    focus:ring-indigo-500 focus:border-indigo-500
                    mt-1
                    block
                    w-full
                    sm:text-sm
                    border border-gray-300
                    rounded-md
                  "
                  placeholder="you@example.com"
                />
              </div>
              <p class="mt-2 text-sm text-gray-500">
                Brief description for your profile. URLs are hyperlinked.
              </p>
            </div> -->
            <!-- <div class="col-span-3">
              <label class="block text-sm font-medium text-gray-700">
                Photo
              </label>
              <div class="mt-1 flex items-center">
                <span
                  class="
                    inline-block
                    bg-gray-100
                    rounded-full
                    overflow-hidden
                    h-12
                    w-12
                  "
                >
                  <svg
                    class="h-full w-full text-gray-300"
                    fill="currentColor"
                    viewBox="0 0 24 24"
                  >
                    <path
                      d="M24 20.993V24H0v-2.996A14.977 14.977 0 0112.004 15c4.904 0 9.26 2.354 11.996 5.993zM16.002 8.999a4 4 0 11-8 0 4 4 0 018 0z"
                    />
                  </svg>
                </span>
                <button
                  type="button"
                  class="
                    ml-5
                    bg-white
                    border border-gray-300
                    rounded-md
                    shadow-sm
                    py-2
                    px-3
                    text-sm
                    leading-4
                    font-medium
                    text-gray-700
                    hover:bg-gray-50
                    focus:outline-none
                    focus:ring-2
                    focus:ring-offset-2
                    focus:ring-indigo-500
                  "
                >
                  Change
                </button>
              </div>
            </div> -->

            <!-- <div class="col-span-3">
              <label class="block text-sm font-medium text-gray-700">
                Cover photo
              </label>
              <div
                class="
                  mt-1
                  border-2 border-gray-300 border-dashed
                  rounded-md
                  px-6
                  pt-5
                  pb-6
                  flex
                  justify-center
                "
              >
                <div class="space-y-1 text-center">
                  <svg
                    class="mx-auto h-12 w-12 text-gray-400"
                    stroke="currentColor"
                    fill="none"
                    viewBox="0 0 48 48"
                    aria-hidden="true"
                  >
                    <path
                      d="M28 8H12a4 4 0 00-4 4v20m32-12v8m0 0v8a4 4 0 01-4 4H12a4 4 0 01-4-4v-4m32-4l-3.172-3.172a4 4 0 00-5.656 0L28 28M8 32l9.172-9.172a4 4 0 015.656 0L28 28m0 0l4 4m4-24h8m-4-4v8m-12 4h.02"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                  </svg>
                  <div class="flex text-sm text-gray-600">
                    <label
                      for="file-upload"
                      class="
                        relative
                        cursor-pointer
                        bg-white
                        rounded-md
                        font-medium
                        text-indigo-600
                        hover:text-indigo-500
                        focus-within:outline-none
                        focus-within:ring-2
                        focus-within:ring-offset-2
                        focus-within:ring-indigo-500
                      "
                    >
                      <span>Upload a file</span>
                      <input
                        id="file-upload"
                        name="file-upload"
                        type="file"
                        class="sr-only"
                      />
                    </label>
                    <p class="pl-1">or drag and drop</p>
                  </div>
                  <p class="text-xs text-gray-500">PNG, JPG, GIF up to 10MB</p>
                </div>
              </div>
            </div> -->
          </div>
        </div>
        <div class="px-4 py-3 bg-gray-50 text-right sm:px-6">
          <button
            type="submit"
            class="
              bg-[#703ED9]
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
              focus:ring-indigo-500
            "
          >
            Save
          </button>
        </div>
      </div>
    </form>

    <!-- <form action="#" method="POST">
      <div class="shadow sm:rounded-md sm:overflow-hidden">
        <div class="bg-white py-6 px-4 space-y-6 sm:p-6">
          <div>
            <h3 class="text-lg leading-6 font-medium text-gray-900">
              Personal Information
            </h3>
            <p class="mt-1 text-sm text-gray-500">
              Use a permanent address where you can recieve mail.
            </p>
          </div>

          <div class="grid grid-cols-6 gap-6">
            <div class="col-span-6 sm:col-span-3">
              <label
                for="first-name"
                class="block text-sm font-medium text-gray-700"
                >First name</label
              >
              <input
                type="text"
                name="first-name"
                id="first-name"
                autocomplete="given-name"
                class="
                  mt-1
                  block
                  w-full
                  border border-gray-300
                  rounded-md
                  shadow-sm
                  py-2
                  px-3
                  focus:outline-none
                  focus:ring-indigo-500
                  focus:border-indigo-500
                  sm:text-sm
                "
              />
            </div>

            <div class="col-span-6 sm:col-span-3">
              <label
                for="last-name"
                class="block text-sm font-medium text-gray-700"
                >Last name</label
              >
              <input
                type="text"
                name="last-name"
                id="last-name"
                autocomplete="family-name"
                class="
                  mt-1
                  block
                  w-full
                  border border-gray-300
                  rounded-md
                  shadow-sm
                  py-2
                  px-3
                  focus:outline-none
                  focus:ring-indigo-500
                  focus:border-indigo-500
                  sm:text-sm
                "
              />
            </div>

            <div class="col-span-6 sm:col-span-4">
              <label
                for="email-address"
                class="block text-sm font-medium text-gray-700"
                >Email address</label
              >
              <input
                type="text"
                name="email-address"
                id="email-address"
                autocomplete="email"
                class="
                  mt-1
                  block
                  w-full
                  border border-gray-300
                  rounded-md
                  shadow-sm
                  py-2
                  px-3
                  focus:outline-none
                  focus:ring-indigo-500
                  focus:border-indigo-500
                  sm:text-sm
                "
              />
            </div>

            <div class="col-span-6 sm:col-span-3">
              <label
                for="country"
                class="block text-sm font-medium text-gray-700"
                >Country</label
              >
              <select
                id="country"
                name="country"
                autocomplete="country-name"
                class="
                  mt-1
                  block
                  w-full
                  bg-white
                  border border-gray-300
                  rounded-md
                  shadow-sm
                  py-2
                  px-3
                  focus:outline-none
                  focus:ring-indigo-500
                  focus:border-indigo-500
                  sm:text-sm
                "
              >
                <option>United States</option>
                <option>Canada</option>
                <option>Mexico</option>
              </select>
            </div>

            <div class="col-span-6">
              <label
                for="street-address"
                class="block text-sm font-medium text-gray-700"
                >Street address</label
              >
              <input
                type="text"
                name="street-address"
                id="street-address"
                autocomplete="street-address"
                class="
                  mt-1
                  block
                  w-full
                  border border-gray-300
                  rounded-md
                  shadow-sm
                  py-2
                  px-3
                  focus:outline-none
                  focus:ring-indigo-500
                  focus:border-indigo-500
                  sm:text-sm
                "
              />
            </div>

            <div class="col-span-6 sm:col-span-6 lg:col-span-2">
              <label for="city" class="block text-sm font-medium text-gray-700"
                >City</label
              >
              <input
                type="text"
                name="city"
                id="city"
                autocomplete="address-level2"
                class="
                  mt-1
                  block
                  w-full
                  border border-gray-300
                  rounded-md
                  shadow-sm
                  py-2
                  px-3
                  focus:outline-none
                  focus:ring-indigo-500
                  focus:border-indigo-500
                  sm:text-sm
                "
              />
            </div>

            <div class="col-span-6 sm:col-span-3 lg:col-span-2">
              <label
                for="region"
                class="block text-sm font-medium text-gray-700"
                >State / Province</label
              >
              <input
                type="text"
                name="region"
                id="region"
                autocomplete="address-level1"
                class="
                  mt-1
                  block
                  w-full
                  border border-gray-300
                  rounded-md
                  shadow-sm
                  py-2
                  px-3
                  focus:outline-none
                  focus:ring-indigo-500
                  focus:border-indigo-500
                  sm:text-sm
                "
              />
            </div>

            <div class="col-span-6 sm:col-span-3 lg:col-span-2">
              <label
                for="postal-code"
                class="block text-sm font-medium text-gray-700"
                >ZIP / Postal code</label
              >
              <input
                type="text"
                name="postal-code"
                id="postal-code"
                autocomplete="postal-code"
                class="
                  mt-1
                  block
                  w-full
                  border border-gray-300
                  rounded-md
                  shadow-sm
                  py-2
                  px-3
                  focus:outline-none
                  focus:ring-indigo-500
                  focus:border-indigo-500
                  sm:text-sm
                "
              />
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
              focus:ring-indigo-500
            "
          >
            Save
          </button>
        </div>
      </div>
    </form> -->

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
} from "@heroicons/vue/outline";

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
      streamURL: "https://stream.kappamon.com/t/2d081ff2-997a-4924-ae26-6c019e1cfb2b",
    };
  },
  methods: {
    copyButton() {
      this.$refs.clone.focus();
      document.execCommand('copy');
      this.copyValue = "Copied!";
      setTimeout(() => {
        this.copyValue = "Copy";
      }, 3000);
    },
  },
};
</script>