<script>
// import countryFlag from './countryFlag';
import CountryFlag from 'vue-country-flag-next'



export default {
    date() {
        return {
        }

    },
    props: {
        cardSeries: Object,
        vote: Number
    },
    components: {
        CountryFlag
    },
    methods: {
        getCountryFlag(lang) {
            const validLang = {
                en: 'gb',
                ja: 'jp',
                ko: 'kr',
                zh: 'cn'

            }
            if (lang in validLang) {
                return validLang[lang]
            }
             else {
                 return lang
            }
            
        }
    },
}
</script>

<template>
<div class="container">
    <div class="card border-0">

        <div class="imgFilm ">
            <img :src="'https://image.tmdb.org/t/p/w300/' + cardSeries.poster_path" :alt="cardSeries.original_name">
        </div>

        <div class="infoFilm ">

            <h3>
                Title: {{ cardSeries.name }} 
                <!-- {{ cardSeries.name }} -->
            </h3>
    
            <h4>
                Original Title: {{ cardSeries.original_name }}
                <!-- {{ cardSeries.original_name }} -->
    
            </h4>
    
            <div>
                {{ cardSeries.original_language }}
                <CountryFlag :country='getCountryFlag(cardSeries.original_language)' size='big'/>
                
            </div>
            <h5>
                <!-- {{ (vote / 2).toFixed(0) }} -->
                <span v-if="(vote / 2).toFixed(0) == 5" >
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star text-warning"></i>
                </span>
    
                <span v-else-if="(vote / 2).toFixed(0) == 4" >
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star"></i>
                </span>
    
                <span v-else-if="(vote / 2).toFixed(0) == 3" >
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star"></i>
                    <i class="fa-solid fa-star"></i>
                </span>
    
                <span v-else-if="(vote / 2).toFixed(0) == 2" >
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star"></i>
                    <i class="fa-solid fa-star"></i>
                    <i class="fa-solid fa-star"></i>
                </span>
    
                <span v-else-if="(vote / 2).toFixed(0) == 1" >
                    <i class="fa-solid fa-star text-warning"></i>
                    <i class="fa-solid fa-star"></i>
                    <i class="fa-solid fa-star"></i>
                    <i class="fa-solid fa-star"></i>
                    <i class="fa-solid fa-star"></i>
                </span>
    
                <span v-else >
                    <i class="fa-solid fa-star"></i>
                    <i class="fa-solid fa-star"></i>
                    <i class="fa-solid fa-star"></i>
                    <i class="fa-solid fa-star"></i>
                    <i class="fa-solid fa-star"></i>
                </span>
            </h5>
    
            <h5>
                Overview: {{ cardSeries.overview }}
            </h5>
        </div>

    </div>

</div>

    
</template>

<style lang="scss" scoped>
.card {
    min-height:  450px;;
}

.card .imgFilm > img {
    width: 100%;
    height: 450px;
    object-fit: cover;
}
.card:hover .imgFilm {
    display: none;
}

.infoFilm {
    display: none;
    > * {
        padding-bottom: 5px;
    }
}

.card:hover .infoFilm {
    display: block;
}
</style>