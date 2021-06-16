<template>
  <select v-model="select" class="form-select block w-full border p-3 rounded mt-10 mb-10" @change="onChange()"> 
      <option value="0">Select Country</option>
      <option v-for="Country in countries" :key="Country.ID" :value="Country.ID"> {{ Country.Country }} </option>
  </select>
</template>

<script>
export default {
    name: 'CountryData',
    props: ['countries'],
    data() {
        return  {
            select: 0,
            // Countries: null
        }
    },
    methods: {
        onChange() {
            const  country = this.countries.find((item) => item.ID === this.select)
            // console.log(country)
            this.$emit('get-country', country)
        }
    }
}
</script>

<style>

</style>