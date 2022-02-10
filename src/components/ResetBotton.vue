<template>
      <button 
      @click="resetData"
      class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600">
         Reset
      </button>
</template>

<script>
export default {
   name: 'ResetBotton',
   props:{
      resetData:Function
   },

}
</script>