<template>
      <div class="text-center">
            <h2 class="text-3xl font-bold">{{text}}</h2>
            <div class="text-2xl mt-4 mb-10">
               {{timeStanp()}}
            </div>
      </div>
</template>

<script>
import moment from 'moment'
export default {
   name: 'DataTittle',
   props: ['text', 'dataDate'],

   methods:{
      timeStanp() {
         return moment(this.dataDate).format('MMM Do YYYY, h:mm:ss a')
      }
   }
}
</script>