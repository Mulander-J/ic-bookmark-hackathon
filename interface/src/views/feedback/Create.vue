<template>
  <div class="p-5">
    <h2 class="pix-h2 flex items-center">      
      <span>SEND REPORT</span>
      <rt-btn class="ml-2" icon="ri-arrow-go-back-line" v-throttle @click="$router.push('/feedback')" />
    </h2>
    <div class="lg:w-1/2 w-full">
      <div class="form-item">
        <label>TYPE</label>
        <select class="slate-widget p-2" v-model="_formData.type" placeholder="Please Select">
          <option value="" selected disabled>-Select Type</option>
          <option value="bug" class="text-rose-500">bug</option>
          <option value="feature" class="text-amber-500">feature</option>
          <option value="suggestion" class="text-lime-500">suggestion</option>
        </select>
      </div>
      <div class="form-item">
        <label>Content</label>
        <textarea class="form-widget slate-widget p-2" v-model.trim="_formData.content" cols="25" rows="5" placeholder="Write down your advice" />
      </div>
      <div class="my-4 text-rose-500" v-show="_errMsg">{{_errMsg}}</div>
      <div class="btn slate-widget font-pixie my-4 w-min py-2 px-8" v-throttle v-sign="addItem">SUBMIT</div>  
    </div>
  </div>
</template>
<script lang="ts" setup>
import { ref, getCurrentInstance } from 'vue'
import { useAuthStore } from "@/store/modules/auth"
import { getInsICXFactory } from '@/hooks/useCanister'

const { proxy } = getCurrentInstance() as any
const authStore = useAuthStore()

const _formData = ref({type:'',content:''})

const _errMsg = ref('')

const addItem = async ()=>{
  if(authStore.getIsLoading) return

  const {content,type} = _formData.value
  if(!type){
    _errMsg.value = 'Type is required.'
    return
  }
  if(!content){
    _errMsg.value = 'Content is required.'
    return
  }
  _errMsg.value = ''

  proxy.$verify({},async (res:boolean)=>{
    if(!res) return
    const payloads = [{[type]:null},content]
    const InsICXFactory = getInsICXFactory(authStore.agent)
    InsICXFactory && await authStore.handleCall({
      name:'Add Feedback',
      cmd:InsICXFactory.insertFeedback,
      okTip:true,
      cbk:()=>{
        _formData.value = {type:'',content:''}
      }, 
    },...payloads)
  })
}
</script>