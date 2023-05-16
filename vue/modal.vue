<template>
  <div v-show="showModal">
    <button type="button"  @click="closeSelf">取消</button>
    <button type="button"  @click="confirm">确认</button>
  </div>
  <button type="button" @click='createModal()'>点击我出现一个Modal</button>

</template>
 
<style>

</style>
 
<script>
export default {
  name: 'Modal',
  data() {
    return {
      showModal:false
    }
  },
  methods: {    
    closeSelf(){
      this.showModal = !this.showModal   
    },
    confirm(){
      this.showModal = !this.showModal  
    },
    createModal(){
      this.showModal = !this.showModal  
    }
  }
}
</script>