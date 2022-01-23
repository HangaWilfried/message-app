<template>
  <main class="w-3/4 mx-auto px-3 pt-10 pb-32 bg-zinc-100">
    <section class="px-4">
      <HeaderMessage2 v-if="!isScrollDown"/>
      <HeaderMessage :totalMessage = "countMessage" v-else/>
      <MenuMessage/>
    </section>
    <section class="bg-white px-4 py-2 rounded-md">
      <NewMessage v-for="(message, index) in messages" :key="index" :author="message.author" :receptionTime="message.time">
        <template #default>
          <span class="text-sm text-zinc-500">{{message.text}}</span>
        </template>
      </NewMessage>
    </section>
    <section class="px-4 flex flex-col">
      <div class="place-self-end bg-blue-600 p-2 rounded-full cursor-pointer">
        <Chat/>
      </div>
      <FooterMessage :totalMessage = "countMessage"/>
    </section>
  </main>
</template>


<script>
import HeaderMessage2 from "./components/header/HeaderMessage2.vue";
import HeaderMessage from "./components/header/HeaderMessage.vue";
import MenuMessage from "./components/MenuMessage.vue";
import NewMessage from "./components/NewMessage.vue";
import FooterMessage from "./components/FooterMessage.vue";
import Chat from './components/Chat.vue'
import {computed, ref, reactive, onMounted} from 'vue'

export default {
  name: 'App',
  components: {Chat, FooterMessage, NewMessage, MenuMessage, HeaderMessage, HeaderMessage2},
  setup(){
    const messages = reactive([
      {
        text: 'bonjour je peux venir chez toi aujourd\'hui',
        author: 'wilfried',
        time: `${new Date().getDate()}/0${new Date().getMonth()+1}/${new Date().getFullYear()}`
      },
      {
        text: 'Soyez le bienvenu chez orange. #144*2#',
        author: '8990',
        time: `${new Date().getDate()}/0${new Date().getMonth()+1}/${new Date().getFullYear()}`
      },
      {
        text: 'Active ton compte sur Ayoba, l\'appli tout en un',
        author: 'Free Chat',
        time: `${new Date().getDate()}/0${new Date().getMonth()+1}/${new Date().getFullYear()}`
      },
      {
        text: 'Vous, WILFRIED JUNIOR HANGA LAGOUE (236...)',
        author: 'Mobile Money',
        time: `${new Date().getDate()}/0${new Date().getMonth()+1}/${new Date().getFullYear()}`
      },
      {
        text: '<#>Votre code de confirmation Twitter &agrave 6 chiffres est le *******',
        author: 'Twitter',
        time: `${new Date().getDate()}/0${new Date().getMonth()+1}/${new Date().getFullYear()}`
      },
      {
        text: 'Ref:822833413 16/01 11:20:51 mtn recu:zaf10000fcfa de 2376743',
        author: '7154',
        time: `${new Date().getDate()}/0${new Date().getMonth()+1}/${new Date().getFullYear()}`
      },
      {
        text: 'Vous avez recu 500f=1.23GB de MTN prolongation. vous serez facture a 575fcfa',
        author: '121',
        time: `${new Date().getDate()}/0${new Date().getMonth()+1}/${new Date().getFullYear()}`
      },
      {
        text: 'Txn:Credit Compte: 1XX.25X Valeur:XAF 2000000',
        author: 'UBA',
        time: `${new Date().getDate()}/0${new Date().getMonth()+1}/${new Date().getFullYear()}`
      }
    ])

    const countMessage = computed(() => messages.length)
    const isScrollDown = ref(false)

    onMounted(() =>{
      window.addEventListener('scroll', ()=>{
        if(scrollY > 2){
          isScrollDown.value = false
        }
        else{
          isScrollDown.value = true
        }
        console.log( isScrollDown.value)
        return isScrollDown.value
      })
    })
    return {
      messages, isScrollDown, countMessage
    }
  }
}
</script>
