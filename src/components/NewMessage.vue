<template>
  <div class="flex space-x-5 items-center my-5">
    <div class="flex flex-col justify-center rounded-full p-3 bg-gradient-to-r from-fuchsia-500 to-blue-500 via-sky-500">
      <Contact class="fill-white w-4 stroke-white"/>
    </div>
    <div class="border-b border-gray-300 pb-2 w-full">
      <div class="flex justify-between w-full mb-1.5 text-gray-900">
        <span class="font-sans font-bold capitalize">{{author}}</span>
        <span>{{receptionTime}}</span>
      </div>
      <div>
        <slot/>
      </div>
    </div>
  </div>
</template>

<script>
import Contact from './Contact.vue'
export default {
  name: "NewMessage",
  components: {Contact},
  props: {
    author: {
      type: String,
      required: true
    },
    receptionTime: {
      type: String,
      required: true
    }
  }
}
</script>
