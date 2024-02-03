<template >
    <div>
        <v-container fluid>
            <v-row>
                <v-col>
                    <RouterLink class="routerLink" to="/">
                        <v-btn class=" px-8">
                            Back
                        </v-btn>
                    </RouterLink>
                </v-col>
            </v-row>
            <v-row class="mt-16 main-details">
                <v-col cols="12" sm="6" md="6" xl="6" class="pr-sm-12 pr-lg-12  pr-xl-12">
                    <v-img class="w-100" aspect-ratio="16/9" cover :src="countryDetails.flag"></v-img>
                </v-col>
                <v-col cols="12" sm="6" md="6" xl="6" class="pl-sm-12 pl-lg-12 pl-xl-12">
                    <h1 class="mt-8">{{ countryDetails.name }}</h1>
                    <v-row>
                        <v-col cols="12" sm="6" md="6" xl="6">
                            <p class="mt-6"> NativeName: {{ countryDetails.nativeName }}</p>
                            <p class="mt-1"> Population: {{ countryDetails.population }}</p>
                            <p class="mt-1"> Region: {{ countryDetails.region }}</p>
                            <p class="mt-1"> SubRegion: {{ countryDetails.subregion }}</p>
                            <p class="mt-1"> Capital: {{ countryDetails.capital }}</p>
                        </v-col>
                        <v-col cols="12" sm="6" md="6" xl="6">
                            <p class="mt-6"> TopLevelDomain: {{ countryDetails.topLevelDomain[0] }}</p>
                            <p class="mt-1"> Currencies: {{ countryDetails.currencies[0].name }}</p>
                            <p class="mt-1"> Languages: <span v-for="item in countryDetails.languages"> {{ item.name }}
                                </span></p>

                        </v-col>



                    </v-row>
                    <v-row class="my-16 pt-10 mx-2 ">
                        
                            <span class="mt-5" > Borders Countries: </span>
                            <v-btn class="mx-1 px-8 mt-4" v-for="item in countryDetails.borders">
                                {{ item }}
                            </v-btn>
                       

                    </v-row>








                </v-col>

            </v-row>
        </v-container>
    </div>
</template>
<script>
import { data } from '../data'

export default {
    data() {
        return {
            routeId: null,
            countryDetails: null

        }
    },
    beforeMount() {
        // Access route parameters in the mounted hook or any other lifecycle hook
        this.routeId = this.$route.params.id;
        this.countryDetails = data[this.routeId];
        console.log('Route ID:', this.countryDetails);
    },
    updated() {
        this.routeId = this.$route.params.id;

        this.countryDetails = data[this.routeId];
    },
}
</script>
<style ></style>