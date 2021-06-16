<template>
<main v-if="!loading">
  <dataTitle :text="title" :dataDate="dataDate"/>
  <dataBox :status="status" />
  <countryData @get-country="getCountryData" :countries="Countries"/>
</main>
<main class="flex flex-col align-center justify-center text-center" v-else>
  <div class="text-gray-500 text-3xl mt-10 mb-6">
    Fecthing Data
  </div>
  <img :src="loadingImage" alt="loader" class="w-100 m-auto">
</main>
</template>

<script>
// @ is an alias to /src
import dataTitle from '@/components/dataTitle.vue'
import dataBox from '@/components/dataBox.vue'
import countryData from '@/components/countryData.vue'

export default {
  name: 'Home',
  components: {
    dataTitle,
    dataBox,
    countryData
  },
  data() {
    return {
      loading: true,
      title: 'Global',
      status: {},
      dataDate: '',
      Countries: [],
      loadingImage: require('../assets/loader.gif')
    }
  },
  methods: {
    async fetchCovidData () {
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    },
    getCountryData(country) {
      this.status = country
      this.title = country.Country
    }
  },
  async created() {
    const data = await this.fetchCovidData()
    console.log(data)
    this.dataDate = data.Date
    this.status = data.Global
    this.Countries = data.Countries
    this.loading = false
  }
}
</script>
