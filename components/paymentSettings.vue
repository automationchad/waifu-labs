<template>
  <div class="space-y-6 sm:px-6 lg:px-0 lg:col-span-9">
    <section aria-labelledby="payment-details-heading">
      <form action="#" method="POST">
        <div class="shadow sm:rounded-md sm:overflow-hidden">
          <div class="bg-white py-6 px-4 sm:p-6">
            <div>
              <h2
                id="payment-details-heading"
                class="text-lg leading-6 font-medium text-gray-900"
              >
                Payment details
              </h2>
              <p class="mt-1 text-sm text-gray-500">
                Update your billing information. Please note that updating your
                location could affect your tax rates.
              </p>
            </div>
            <div v-if="cardDetails" class="mt-5">
              <div
                class="
                  rounded-md
                  bg-gray-50
                  px-6
                  py-5
                  sm:flex sm:items-start sm:justify-between
                "
              >
                <h4 class="sr-only">Visa</h4>
                <div class="sm:flex sm:items-start">
                  <svg
                    class="h-8 w-auto sm:flex-shrink-0 sm:h-6"
                    viewBox="0 0 36 24"
                    aria-hidden="true"
                  >
                    <rect width="36" height="24" fill="#224DBA" rx="4" />
                    <path
                      fill="#fff"
                      d="M10.925 15.673H8.874l-1.538-6c-.073-.276-.228-.52-.456-.635A6.575 6.575 0 005 8.403v-.231h3.304c.456 0 .798.347.855.75l.798 4.328 2.05-5.078h1.994l-3.076 7.5zm4.216 0h-1.937L14.8 8.172h1.937l-1.595 7.5zm4.101-5.422c.057-.404.399-.635.798-.635a3.54 3.54 0 011.88.346l.342-1.615A4.808 4.808 0 0020.496 8c-1.88 0-3.248 1.039-3.248 2.481 0 1.097.969 1.673 1.653 2.02.74.346 1.025.577.968.923 0 .519-.57.75-1.139.75a4.795 4.795 0 01-1.994-.462l-.342 1.616a5.48 5.48 0 002.108.404c2.108.057 3.418-.981 3.418-2.539 0-1.962-2.678-2.077-2.678-2.942zm9.457 5.422L27.16 8.172h-1.652a.858.858 0 00-.798.577l-2.848 6.924h1.994l.398-1.096h2.45l.228 1.096h1.766zm-2.905-5.482l.57 2.827h-1.596l1.026-2.827z"
                    />
                  </svg>
                  <div class="mt-3 sm:mt-0 sm:ml-4">
                    <div class="text-sm font-medium text-gray-900">
                      Ending with 4242
                    </div>
                    <div
                      class="mt-1 text-sm text-gray-600 sm:flex sm:items-center"
                    >
                      <div>Expires 12/20</div>
                      <span class="hidden sm:mx-2 sm:inline" aria-hidden="true">
                        &middot;
                      </span>
                      <div class="mt-1 sm:mt-0">
                        Last updated on 22 Aug 2017
                      </div>
                    </div>
                  </div>
                </div>
                <div class="mt-4 sm:mt-0 sm:ml-6 sm:flex-shrink-0">
                  <button
                    type="button"
                    class="
                      inline-flex
                      items-center
                      px-4
                      py-2
                      border border-gray-300
                      shadow-sm
                      font-medium
                      rounded-md
                      text-gray-700
                      bg-white
                      hover:bg-gray-50
                      focus:outline-none
                      focus:ring-2
                      focus:ring-offset-2
                      focus:ring-indigo-500
                      sm:text-sm
                    "
                  >
                    Edit
                  </button>
                </div>
              </div>
            </div>
            <div v-else class="mt-6 grid grid-cols-4 gap-6">
              <div class="col-span-2">
                <fieldset>
                  <legend class="block text-sm font-medium text-gray-700">
                    Card Details
                  </legend>
                  <div class="mt-1 bg-white rounded-md shadow-sm -space-y-px">
                    <div>
                      <label for="card-number" class="sr-only"
                        >Card number</label
                      >
                      <input
                        type="text"
                        name="card-number"
                        id="card-number"
                        class="
                          focus:ring-indigo-500 focus:border-indigo-500
                          relative
                          block
                          w-full
                          rounded-none rounded-t-md
                          bg-transparent
                          focus:z-10
                          sm:text-sm
                          border-gray-300
                        "
                        placeholder="Card number"
                      />
                    </div>
                    <div class="flex -space-x-px">
                      <div class="w-1/2 flex-1 min-w-0">
                        <label for="card-expiration-date" class="sr-only"
                          >Expiration date</label
                        >
                        <input
                          type="text"
                          name="card-expiration-date"
                          id="card-expiration-date"
                          class="
                            focus:ring-indigo-500 focus:border-indigo-500
                            relative
                            block
                            w-full
                            rounded-none rounded-bl-md
                            bg-transparent
                            focus:z-10
                            sm:text-sm
                            border-gray-300
                          "
                          placeholder="MM / YY"
                        />
                      </div>
                      <div class="flex-1 min-w-0">
                        <label for="card-cvc" class="sr-only">CVC</label>
                        <input
                          type="text"
                          name="card-cvc"
                          id="card-cvc"
                          class="
                            focus:ring-indigo-500 focus:border-indigo-500
                            relative
                            block
                            w-full
                            rounded-none rounded-br-md
                            bg-transparent
                            focus:z-10
                            sm:text-sm
                            border-gray-300
                          "
                          placeholder="CVC"
                        />
                      </div>
                    </div>
                  </div>
                </fieldset>
              </div>
              <div class="col-span-2">
                <fieldset class="bg-white">
                  <legend class="block text-sm font-medium text-gray-700">
                    Billing address
                  </legend>
                  <div class="mt-1 rounded-md shadow-sm -space-y-px">
                    <div>
                      <label for="country" class="sr-only">Country</label>
                      <select
                        id="country"
                        name="country"
                        autocomplete="country-name"
                        class="
                          focus:ring-indigo-500 focus:border-indigo-500
                          relative
                          block
                          w-full
                          rounded-none rounded-t-md
                          bg-transparent
                          focus:z-10
                          sm:text-sm
                          border-gray-300
                        "
                      >
                        <option>United States</option>
                        <option>Canada</option>
                        <option>Mexico</option>
                      </select>
                    </div>
                    <div>
                      <label for="postal-code" class="sr-only"
                        >ZIP / Postal code</label
                      >
                      <input
                        type="text"
                        name="postal-code"
                        id="postal-code"
                        autocomplete="postal-code"
                        class="
                          focus:ring-indigo-500 focus:border-indigo-500
                          relative
                          block
                          w-full
                          rounded-none rounded-b-md
                          bg-transparent
                          focus:z-10
                          sm:text-sm
                          border-gray-300
                        "
                        placeholder="ZIP / Postal code"
                      />
                    </div>
                  </div>
                </fieldset>
              </div>
            </div>
          </div>
          <div class="px-4 py-3 bg-gray-50 text-right sm:px-6">
            <button
              type="submit"
              class="
                bg-gray-800
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
                hover:bg-gray-900
                focus:outline-none
                focus:ring-2
                focus:ring-offset-2
                focus:ring-gray-900
              "
            >
              Save
            </button>
          </div>
        </div>
      </form>
    </section>

    <!-- Plan -->
    <section aria-labelledby="plan-heading">
      <form action="#" method="POST">
        <div class="shadow sm:rounded-md sm:overflow-hidden">
          <div class="bg-white py-6 px-4 space-y-6 sm:p-6">
            <div>
              <h2
                id="plan-heading"
                class="text-lg leading-6 font-medium text-gray-900"
              >
                Plan
              </h2>
            </div>

            <RadioGroup v-model="selectedPlan">
              <RadioGroupLabel class="sr-only"> Pricing plans </RadioGroupLabel>
              <div class="relative bg-white rounded-md -space-y-px">
                <RadioGroupOption
                  as="template"
                  v-for="(plan, planIdx) in plans"
                  :key="plan.name"
                  :value="plan"
                  v-slot="{ checked, active }"
                >
                  <div
                    :class="[
                      planIdx === 0 ? 'rounded-tl-md rounded-tr-md' : '',
                      planIdx === plans.length - 1
                        ? 'rounded-bl-md rounded-br-md'
                        : '',
                      checked
                        ? 'bg-orange-50 border-orange-200 z-10'
                        : 'border-gray-200',
                      'relative border p-4 flex flex-col cursor-pointer md:pl-4 md:pr-6 md:grid md:grid-cols-3 focus:outline-none',
                    ]"
                  >
                    <span class="flex items-center text-sm">
                      <span
                        :class="[
                          checked
                            ? 'bg-orange-500 border-transparent'
                            : 'bg-white border-gray-300',
                          active ? 'ring-2 ring-offset-2 ring-gray-900' : '',
                          'h-4 w-4 rounded-full border flex items-center justify-center',
                        ]"
                        aria-hidden="true"
                      >
                        <span class="rounded-full bg-white w-1.5 h-1.5" />
                      </span>
                      <RadioGroupLabel
                        as="span"
                        class="ml-3 font-medium text-gray-900"
                        >{{ plan.name }}</RadioGroupLabel
                      >
                    </span>
                    <RadioGroupDescription
                      as="span"
                      class="ml-6 pl-1 text-sm md:ml-0 md:pl-0 md:text-center"
                    >
                      <span
                        :class="[
                          checked ? 'text-orange-900' : 'text-gray-900',
                          'font-medium',
                        ]"
                        >${{ plan.priceMonthly }} / mo</span
                      >
                      {{ " " }}
                      <span
                        :class="checked ? 'text-orange-700' : 'text-gray-500'"
                        >(${{ plan.priceYearly }} / yr)</span
                      >
                    </RadioGroupDescription>
                    <RadioGroupDescription
                      as="span"
                      :class="[
                        checked ? 'text-orange-700' : 'text-gray-500',
                        'ml-6 pl-1 text-sm md:ml-0 md:pl-0 md:text-right',
                      ]"
                      >{{ plan.limit }}</RadioGroupDescription
                    >
                  </div>
                </RadioGroupOption>
              </div>
            </RadioGroup>

            <SwitchGroup as="div" class="flex items-center">
              <Switch
                v-model="annualBillingEnabled"
                :class="[
                  annualBillingEnabled ? 'bg-orange-500' : 'bg-gray-200',
                  'relative inline-flex flex-shrink-0 h-6 w-11 border-2 border-transparent rounded-full cursor-pointer focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-900 transition-colors ease-in-out duration-200',
                ]"
              >
                <span
                  aria-hidden="true"
                  :class="[
                    annualBillingEnabled ? 'translate-x-5' : 'translate-x-0',
                    'inline-block h-5 w-5 rounded-full bg-white shadow transform ring-0 transition ease-in-out duration-200',
                  ]"
                />
              </Switch>
              <SwitchLabel as="span" class="ml-3">
                <span class="text-sm font-medium text-gray-900"
                  >Annual billing
                </span>
                <span class="text-sm text-gray-500">(Save 10%)</span>
              </SwitchLabel>
            </SwitchGroup>
          </div>
          <div class="px-4 py-3 bg-gray-50 text-right sm:px-6">
            <button
              type="submit"
              class="
                bg-gray-800
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
                hover:bg-gray-900
                focus:outline-none
                focus:ring-2
                focus:ring-offset-2
                focus:ring-gray-900
              "
            >
              Save
            </button>
          </div>
        </div>
      </form>
    </section>

    <!-- Billing history -->
    <section aria-labelledby="billing-history-heading">
      <div class="bg-white pt-6 shadow sm:rounded-md sm:overflow-hidden">
        <div class="px-4 sm:px-6">
          <h2
            id="billing-history-heading"
            class="text-lg leading-6 font-medium text-gray-900"
          >
            Billing history
          </h2>
        </div>
        <div class="mt-6 flex flex-col">
          <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
            <div
              class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8"
            >
              <div class="overflow-hidden border-t border-gray-200">
                <table class="min-w-full divide-y divide-gray-200">
                  <thead class="bg-gray-50">
                    <tr>
                      <th
                        scope="col"
                        class="
                          px-6
                          py-3
                          text-left text-sm
                          font-semibold
                          text-gray-900
                        "
                      >
                        Date
                      </th>
                      <th
                        scope="col"
                        class="
                          px-6
                          py-3
                          text-left text-sm
                          font-semibold
                          text-gray-900
                        "
                      >
                        Description
                      </th>
                      <th
                        scope="col"
                        class="
                          px-6
                          py-3
                          text-left text-sm
                          font-semibold
                          text-gray-900
                        "
                      >
                        Amount
                      </th>
                      <!--
                              `relative` is added here due to a weird bug in Safari that causes `sr-only` headings to introduce overflow on the body on mobile.
                            -->
                      <th
                        scope="col"
                        class="
                          relative
                          px-6
                          py-3
                          text-left text-sm
                          font-medium
                          text-gray-500
                        "
                      >
                        <span class="sr-only">View receipt</span>
                      </th>
                    </tr>
                  </thead>
                  <tbody class="bg-white divide-y divide-gray-200">
                    <tr v-for="payment in payments" :key="payment.id">
                      <td
                        class="
                          px-6
                          py-4
                          whitespace-nowrap
                          text-sm
                          font-medium
                          text-gray-900
                        "
                      >
                        <time :datetime="payment.datetime">{{
                          payment.date
                        }}</time>
                      </td>
                      <td
                        class="
                          px-6
                          py-4
                          whitespace-nowrap
                          text-sm text-gray-500
                        "
                      >
                        {{ payment.description }}
                      </td>
                      <td
                        class="
                          px-6
                          py-4
                          whitespace-nowrap
                          text-sm text-gray-500
                        "
                      >
                        {{ payment.amount }}
                      </td>
                      <td
                        class="
                          px-6
                          py-4
                          whitespace-nowrap
                          text-right text-sm
                          font-medium
                        "
                      >
                        <a
                          :href="payment.href"
                          class="text-orange-600 hover:text-orange-900"
                          >View receipt</a
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
    </section>
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

const plans = [
  {
    name: "Startup",
    priceMonthly: 29,
    priceYearly: 290,
    limit: "Up to 5 active job postings",
  },
  {
    name: "Business",
    priceMonthly: 99,
    priceYearly: 990,
    limit: "Up to 25 active job postings",
  },
  {
    name: "Enterprise",
    priceMonthly: 249,
    priceYearly: 2490,
    limit: "Unlimited active job postings",
  },
];
const payments = [
  {
    id: 1,
    date: "1/1/2020",
    datetime: "2020-01-01",
    description: "Business Plan - Annual Billing",
    amount: "CA$109.00",
    href: "#",
  },
  // More payments...
];

const selectedPlan = ref(plans[1]);
const annualBillingEnabled = ref(true);
const cardDetails = Math.random() > 0.5;
</script>