<template>
  <div class="flex justify-between mt-10 mb-5">
    <button :class="{
      'text-gray-900 border border-gray-900 rounded-full py-2 px-14': !hasClicked,
      'text-gray-600 py-2 px-14': hasClicked
      }" @click="hasClicked=false">Tous</button>
    <button :class="{
      'text-gray-600 px-4 py-2': !hasClicked,
      'text-gray-900 border border-gray-900 rounded-full px-4 py-2': hasClicked
      }" @click="hasClicked = true">Nouvelle cat&eacute;gorie</button>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: "MenuMessage",
  setup(){
    const hasClicked = ref(false)
    return{
      hasClicked
    }
  }
}
</script>
