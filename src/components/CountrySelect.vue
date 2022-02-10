<template>
      <select v-model="selected"  @change="onChange" class="form-select mt-10 block w-full border p-3 rounded">
            <option value="0">Select Country</option>
            <option v-for="(country, i) in countries" :key="i" :value="country.ID">
               {{country.Country}}
            </option>
      </select>
</template>

<script>
export default {
      name: 'CountrySelect',
      props: {
         countries:Object
      },
      data() {
         return {
            selected: 0
         }
      },
      methods:{
         onChange() {
            const countryId = this.countries.find(item => item.ID === this.selected);
            // console.log(countryId)
            return this.$emit('get-selcted', countryId )
         },
      }
}
</script>