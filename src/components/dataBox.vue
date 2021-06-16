<template>
  <div class="grid md:grid-cols-3 gap-4">
      <!-- Box 1 -->
      <div class="shadow-md bg-blue-600 p-10 text-center rounded">
          <h3 class="text-3xl font-bold text-white mb-4">
              Cases
          </h3>
          <div class="text-2xl mb-4 text-white">
              <span class="font-bold">New:</span>
              {{ formatNumber(status.NewConfirmed) }}
              {{ status.CountryCode }}
          </div>
          <div class="text-2xl mb-4 text-white">
              <span class="font-bold">Total:</span>
              {{ formatNumber(status.TotalConfirmed) }}
          </div>
      </div>
      <!-- Box 2 -->
      <div class="shadow-md bg-red-600 p-10 text-center rounded">
          <h3 class="text-3xl font-bold text-white mb-4">
              Death
          </h3>
          <div class="text-2xl mb-4 text-white">
              <span class="font-bold">New:</span>
              {{ formatNumber(status.NewDeaths) }}
          </div>
          <div class="text-2xl mb-4 text-white">
              <span class="font-bold">Total:</span>
              {{ formatNumber(status.TotalDeaths) }}
          </div>
      </div>
      <!-- Box 3 -->
      <div class="shadow-md bg-green-600 p-10 text-center rounded">
          <h3 class="text-3xl font-bold text-white mb-4">
              Recoveries
          </h3>
          <div class="text-2xl mb-4 text-white">
              <span class="font-bold">New:</span>
              {{ formatNumber(status.NewRecovered) }}
          </div>
          <div class="text-2xl mb-4 text-white">
              <span class="font-bold">Total:</span>
              {{ formatNumber(status.TotalRecovered) }}
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'DataBox',
    props: ['status'],
    methods: {
        formatNumber(x) {
            return x.toLocaleString()
        }
    }

}
</script>

<style>

</style>