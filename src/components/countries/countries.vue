<!--Agregamos el codigo alfa 2 para que represente cada uno de los elementos-->

<template>

<div class="container">
  <div class="row">
    <p>Codigo Alfa 2</p>
    <div class="col">
        {{ loadData.map((d) => d.cca2) }}
    </div>
    <p>Codigo Alfa 3</p>
    <div class="col">
        {{ loadData.map((d) => d.cca3) }}
    </div>
    <p>Codigo cioc</p>
    <div class="col">
        {{ loadData.map((d) => d.cioc) }}
    </div>
  </div>
</div>
    
</template>

<script>
import requests from './requests';

export default({
    data(){
        return {
            data: [],
            firstIndex: 0,
            lastIndex: 0,
            sliceData: []
        }
    },
    methods: {
        async getAllCountries(){
            const response = await fetch(requests.getAllCountries);
            this.data = await response.json();
            this.total = this.data.length;
        },
        async getbyRegion(){
            const response = await fetch(requests.getbyRegion(this.$store.state.currentRegion));
            this.data = await response.json();
            this.total = this.data.length;
        }
    },
    computed: {
        loadData(){
            if(this.$store.state.currentRegion == "All"){
                this.getAllCountries()
                this.lastIndex = this.$store.state.currentPage * 10;
                this.firstIndex = this.lastIndex - 10;
                this.sliceData = this.data.slice(this.firstIndex, this.lastIndex)
            } else {
                this.getbyRegion()
                this.lastIndex = this.$store.state.currentPage * 10;
                this.firstIndex = this.lastIndex - 10;
                this.sliceData = this.data.slice(this.firstIndex, this.lastIndex)
            }
            return this.sliceData
        },
        total: {
            get(){
                return this.$store.state.total
            },
            set(value) {
                this.$store.commit("SET_TOTAL",value)
            }
        }
    }
});

</script>
