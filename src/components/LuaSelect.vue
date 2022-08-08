<script setup>
import { ref, toRefs } from "vue";
import {
  Listbox,
  ListboxButton,
  ListboxOptions,
  ListboxOption,
} from "@headlessui/vue";
import { CheckIcon, SelectorIcon } from "@heroicons/vue/solid";

const props = defineProps({
  label: {
    type: String,
    required: true,
  },
  options: {
    type: Array,
    required: true
  },
  multiple: {
    type: Boolean,
    default: false
  }
});

const { options, multiple } = toRefs(props);
const selection = ref(options.value[0]);
</script>

<template>
  <Listbox v-model="selection" :multiple="multiple">
    <div class="mt-4 text-slate-500 text-sm">
      {{ label }}
    </div>
    <div class="relative mt-1">
      <ListboxButton
        class="text-white relative w-full cursor-default rounded-sm py-2 pl-3 pr-10 text-left sm:text-sm border border-solid border-slate-600"
      >
        <span class="block truncate">{{ selection }}</span>
        <span
          class="pointer-events-none absolute inset-y-0 right-0 flex items-center pr-2"
        >
          <SelectorIcon class="h-5 w-5 text-gray-400" aria-hidden="true" />
        </span>
      </ListboxButton>

      <transition
        leave-active-class="transition duration-100 ease-in"
        leave-from-class="opacity-100"
        leave-to-class="opacity-0"
      >
        <ListboxOptions
          class="absolute max-h-60 w-full overflow-auto rounded-sm bg-slate-700 py-1 ring-1 ring-black ring-opacity-5 focus:outline-none sm:text-sm border border-solid border-slate-600"
        >
          <ListboxOption
            v-slot="{ active, selected }"
            v-for="person in options"
            :key="person"
            :value="person"
            as="template"
          >
            <li
              :class="[
                active ? 'bg-slate-100 text-gray-700' : 'text-gray-400',
                'relative cursor-default select-none py-2 pl-10 pr-4',
              ]"
            >
              <span
                :class="[
                  selected ? 'text-slate-200' : 'font-normal',
                  'block truncate',
                ]"
                >{{ person }}</span
              >
              <span
                v-if="selected"
                class="absolute inset-y-0 left-0 flex items-center pl-3 text-white"
              >
                <CheckIcon class="h-5 w-5" aria-hidden="true" />
              </span>
            </li>
          </ListboxOption>
        </ListboxOptions>
      </transition>
    </div>
  </Listbox>
</template>
