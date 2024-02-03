<template >
    <div>
        <RouterLink class="routerLink" :to="`CountryDetails/${cardIndex}`">
        <v-card class="mx-auto w-25" min-width="300"  >
            <v-img class="align-end text-white" height="200" :src="cardData.flag" cover>
            </v-img>
            <div class="py-6">
                <v-card-subtitle class="pb-4">
                    {{ cardData.name }}

                </v-card-subtitle>
                <div class="pl-4 ">
                    Population : {{ cardData.population }}
                </div>
                <div class="pl-4 ">
                    Region : {{ cardData.region }}
                </div>
                <div class="pl-4 ">
                    Capital : {{ cardData.capital }}
                </div>
            </div>
        </v-card>
    </RouterLink>
    </div>
</template>
<script>
export default {
    props: ['cardData', 'cardIndex'],
    mounted() {
        
    }

}
</script>
<style lang="css">
 .routerLink{
     text-decoration: none;
 }

    
</style>