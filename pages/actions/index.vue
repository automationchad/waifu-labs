<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <div class="w-full bg-black min-h-screen items-center justify-center">
    <div class="mx-[250px] justify-center">
      <Triggers/>
      <Rewards/>
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
