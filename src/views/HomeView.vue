<script>
import axios from 'axios';
import { data } from '../data'
import CountryCard from '../components/CountryCard.vue'

export default {
  components: {
    CountryCard,

  },
  data() {
    return {
      countryTopTen: data,
      countrymodel: null,
      countrysearch: null,
      countryFilterRegion: null,
      notfound: false,

      loaded: false,
      loading: false,
      items: ['Asia', 'Europe', 'Africa', 'Oceania', 'Americas'],
    }
  },
  methods: {
    onClick() {
      this.loading = true

      setTimeout(() => {
        this.loading = false
        this.loaded = true
      }, 2000)
    },

    countryFilter() {
      this.countryFilterRegion = this.countryTopTen.filter((res) => {
        return this.countrymodel !== null ? res.region == this.countrymodel : res
      })
    },
    searchCountry() {
      console.log("Europe", this.countrysearch);
      this.countryFilterRegion = this.countryTopTen.filter((res) => {
        return res.name.toLowerCase().includes(this.countrysearch)
      })
      if (this.countryFilterRegion.length == 0) {
        this.notfound = true
      } else {
        this.notfound = false
      }
      // console.log("vvvvv" ,  this.notfound , this.countryFilterRegion   );
    }
  },
  mounted() {
    this.countryFilter()

  }

}


</script>

<template>
  <main>

    <v-container fluid>

      <v-row  no-gutters justify="space-between">
        <v-col cols="12" align-self="center" xs="12" sm="6"  >
          <v-card-text class="  ">
            <v-text-field v-model="countrysearch" :loading="loading" class=" mx-8 search-country" density="compact"
              variant="solo" label="search for a country ..." append-inner-icon="mdi-magnify" single-line hide-details
              @click:append-inner="searchCountry()"></v-text-field>
          </v-card-text>
        </v-col>
        <v-col cols="12" align-self="center" sm="3" xs="12">
          <div class=" mx-12  mt-sm-1 mt-md-1 mt-lg-1 mt-8   ">
            <v-select label="Filter by Region"   class="" v-model="countrymodel" @update:modelValue="countryFilter()" :items="items"
              variant="solo"></v-select>
          </div>
        </v-col>

      </v-row>
      <div v-if="notfound" class="d-flex justify-center mt-16">
        country not found
      </div>
      <div class="d-flex flex-wrap justify-center " v-else>
        <CountryCard class="flex-1-1 ma-6" v-for="(item, index) in countryFilterRegion" :key="index" :cardData="item" 
          :cardIndex="index">
        </CountryCard>
      </div>
    </v-container>
  </main>
</template>
<style>
.search-country .v-field__field {
  height: 50px;
}
</style>
