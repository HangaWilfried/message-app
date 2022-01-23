<template>
  <div class="flex flex-col gap-y-14">
    <div class="place-self-center flex flex-col items-center">
      <h1 class="text-3xl font-normal">Messages</h1>
      <p class="font-sans">{{indication}}</p>
    </div>
    <div class="place-self-end flex justify-center space-x-3 items-center">
      <img src="../../assets/magnifying-glass.png" class="w-7 h-7">
      <img src="../../assets/more.png" class="w-4 h-4">
    </div>
  </div>
</template>

<script>
import {computed} from "vue";

export default {
  name: "HeaderMessage",
  props: {
    totalMessage: {
      type: Number,
      require: true
    }
  },
  setup(props){
    const indication = computed(()=>{
      if(props.totalMessage === 1){
        return `${props.totalMessage} non lu`
      }
      else if(props.totalMessage > 1){
        return `${props.totalMessage} non lus`
      }
      else{
        return 'Aucun message non lu'
      }
    })

    return {indication}
  }
}
</script>
