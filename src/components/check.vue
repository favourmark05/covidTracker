<template>
    <div class="container">
        <h1>This is teh covid 19 App</h1>
        <!-- for cases  -->
    <p> New cases: {{ content.Global.NewConfirmed }} </p>
    <p> Total cases: {{ content.Global.TotalConfirmed }} </p>

    <!-- For Deaths -->
    <p> New Deaths: {{ content.Global.NewDeaths }} </p>
    <p> Total Deaths: {{ content.Global.TotalDeaths }} </p>

    <!-- For Recoveries -->
    <p> New Recoveries: {{ content.Global.NewRecovered }} </p>
    <p> Total recoveries: {{ content.Global.TotalRecovered }} </p>

    <!-- select box for countries -->
    <div class="form-group">
      <label for=""></label>
      <select class="form-control" name="" id="">
        <option v-for="(country, index) in countries" :key="index"> {{ country.Country }} </option>
      </select>
    </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return{
            content: null,
            countries: null,
        }
    },
    methods: {
        getData(){
            axios.get('https://api.covid19api.com/summary')
            .then(res=>{
                this.content = res.data;
                this.countries = res.data.Countries;
                console.log(res.data.Countries)
            })
        }
    },
    mounted(){
        this.getData()
    }
}
</script>

<style scoped>

</style>