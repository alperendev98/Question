<template>
    <b-select placeholder="Select a subject">
        <option v-for="(county, index) in arrayOfCounty" :key="index" :value="county.name">{{county.name}}</option>

    </b-select>

</template>

<script>
    export default {
        data() {
            return {
                isPublic: true,
                selectedCounty : {name:"None"},
                arrayOfCounty : [ {name:'Alameda'}, {name:'Alpine'}, {name:'Amador'}, {name:'Butte'}, {name:'Calaveras'}, {name:'Colusa'}, {name:'Contra Costa'}, {name:'Del Norte'}, {name:'El Dorado'}, {name:'Fresno'}, {name:'Glenn'}, {name:'Humboldt'}, {name:'Imperial'}, {name:'Inyo'}, {name:'Kern'}, {name:'Kings'}, {name:'Lake'}, {name:'Lassen'}, {name:'Los Angeles'}, {name:'Madera'}, {name:'Marin'}, {name:'Mariposa'}, {name:'Mendocino'}, {name:'Merced'}, {name:'Modoc'}, {name:'Mono'}, {name:'Monterey'}, {name:'Napa'}, {name:'Nevada'}, {name:'Orange'}, {name:'Placer'}, {name:'Plumas'}, {name:'Riverside'}, {name:'Sacramento'}, {name:'San Benito'}, {name:'San Bernardino'}, {name:'San Diego'}, {name:'San Francisco'}, {name:'San Joaquin'}, {name:'San Luis Obispo'}, {name:'San Mateo'}, {name:'Santa Barbara'}, {name:'Santa Clara'}, {name:'Santa Cruz'}, {name:'Shasta'}, {name:'Sierra'}, {name:'Siskiyou'}, {name:'Solano'}, {name:'Sonoma'}, {name:'Stanislaus'}, {name:'Sutter'}, {name:'Tehama'}, {name:'Trinity'}, {name:'Tulare'}, {name:'Tuolumne'}, {name:'Ventura'}, {name:'Yolo'}, {name:'Yuba'}],
            
           
            }
        }
    }
</script>