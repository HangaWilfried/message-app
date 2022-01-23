<template>
    <div class="flex justify-between px-20">
      <div
      :class="{
          ' cursor-pointer text-zinc-600 font-medium relative': toggle,
          ' cursor-pointer relative font-bold text-blue-500 border-b border-b-2 border-dashed border-blue-500 font-thin': !toggle
        }"
        @click="toggle=false"
      >
        <span class="p-3 absolute top-0 left-[100px] w-4 h-4 rounded-full justify-center items-center flex flex-col text-gray-100 text-sm font-bold"
          :class="{
            'bg-blue-600': !toggle,
            'bg-zinc-400': toggle
          }"
        >
          {{totalMessage}}
        </span>
        Discussions
      </div>
      <div
      :class="{
          ' cursor-pointer text-zinc-600 font-medium': !toggle,
          ' cursor-pointer relative font-bold text-blue-500 border-b border-b-2 border-dashed border-blue-500 font-thin': toggle
        }"
        @click="toggle=true"
      >
        Contacts
      </div>
    </div>
</template>

<script>
import {ref} from 'vue'
export default {
  name: "FooterMessage",
  props: {
    totalMessage: {
      type: Number,
      require: true
    }
  },
  setup(){
    const toggle = ref(false)
    return {
      toggle
    }
  }
}
</script>
