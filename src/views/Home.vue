<template>
    <main v-if="!loading">
        <DataTitle :text="title" :dataDate="dataDate" />

        <DataBoxes :status="status" />

        <CountrySelect v-on:get-selcted="getCountry" :countries="countries"  />

        <ResetBotton
          v-if="status.Country"
          :resetData="resetDatas"
         /> 
    </main>

    <main v-else class="flex flex-col align-center text-center justify-center" >
        <div class="text-gray-500 text-3xl mt-10 mb-6">
            Fetching
        </div>
        <img :src="loadingImages" class="w-24 m-auto" alt="">
    </main>
</template>

<script>
import DataTitle from '@/components/DataTitle.vue'
import DataBoxes from '@/components/DataBoxes.vue'
import CountrySelect from '@/components/CountrySelect.vue'
import ResetBotton from '@/components/ResetBotton.vue'
export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
    ResetBotton
  },
  data() {
    return {
      loading: true,
      title: 'Global', 
      dataDate: '',
      status: {},
      dataAll: {},
      countries: [],
      loadingImages: require('../assets/loading.gif')
    }
  },
  methods: {
    fetchData() {
      fetch('https://api.covid19api.com/summary')
      .then( res => res.json())
      .then(data => {
       this.dataAll = data
       this.dataDate = data.Date
       this.status = data.Global
       this.countries = data.Countries
       this.loading = false     
      })
    },
    getCountry(countryId) {
       this.status = countryId
      this.title = countryId.Country
    },
    resetDatas() {
        this.loading = true     
      fetch('https://api.covid19api.com/summary')
      .then( res => res.json())
      .then(data => {
       this.dataAll = data
       this.dataDate = data.Date
       this.status = data.Global
       this.countries = data.Countries
      this.title = 'Global'
       this.loading = false     
      })


    }
  },
  created() {
   return this.fetchData()
  }
}
</script>
