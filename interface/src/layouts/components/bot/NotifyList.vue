<template>
  <transition name="fade" mode="out-in" class="notify-rows" tag="div">    
    <transition-group v-show="msgShow" name="slide" mode="out-in">
      <div class="notifyer" :class="getNotifyCls(ms.type)" v-for="ms in authStore.icMsgs" :key="ms.key">            
        <v-icon
          class="notify-del" name="io-close"
          @click="authStore.removeMsg(ms.key)"
        />
        <div class="text" :title="ms.text">{{ms.text}}</div>
      </div>
    </transition-group>
  </transition>
  <div class="my-2 grid grid-cols-3 gap-x-4 items-center" v-if="msgZero>0">    
    <div class="slate-widget btn icoBtn" @click="msgShow = !msgShow">
      <v-icon :flip="msgShow?'horizontal':'vertical'" name="md-expandmore-round" title="Expand"/>
    </div>
    <div>
      <span class="mr-2">{{msgZero}}</span>
      <v-icon flip="horizontal" name="io-chatbox-ellipses" />
    </div>
    <div class="slate-widget btn icoBtn" @click="authStore.clearMsg">
      <v-icon name="io-trash-bin" title="Clear" animation="ring" hover/>
    </div>
  </div>
</template>
<script lang="ts" setup>
import { ref, computed, watch } from 'vue'
import { useAuthStore } from '@/store/modules/auth'
import { MessageType } from '@/model/msg';

const authStore = useAuthStore()

const msgShow = ref(true)
const msgZero = computed(()=>authStore.icMsgs.length||0)
watch(()=>authStore.icMsgs,(s)=>{
  if(s.length>0){
    msgShow.value = true
  }
},{deep:true})

const getNotifyCls = (type:number)=>{
  return `notify-`+ (
    type in MessageType ? ["info","success","warn","error"]?.[type] : "info"
  )
}
</script>
<style>
.notify-rows{
  @apply flex flex-col grow justify-end items-end w-full mr-12;
}
.notifyer{
  @apply relative rounded-md p-2 my-2 text-left w-max flex items-center justify-center select-none;
  margin-top: 1rem;
  background: rgba(0,0,0,.2);
  font-size: 14px;
}
.notifyer .text{
  @apply break-all truncate;
  max-width: 30em;
}

.notify-del{
  @apply mr-2 cursor-pointer;
  width: 1em;
  height: 1em;
  transition: all .3s;
}
.notify-del:hover{
  transform: scale(1.2) rotate(90deg);
}

.notify-info{
  @apply bg-blue-400/[.8];
}
.notify-success{
  @apply bg-green-400/[.8];
}
.notify-warn{
  @apply bg-amber-400/[.8];
}
.notify-error{
  @apply bg-rose-400/[.8];
}
</style>