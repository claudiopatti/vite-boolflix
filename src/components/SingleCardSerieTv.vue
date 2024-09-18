<script>
// import countryFlag from './countryFlag';
import CountryFlag from 'vue-country-flag-next'



export default {
    data() {
        return {
            urlInitials: "https://image.tmdb.org/t/p/",
            sizeUrl: 'w342'
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
    
    computed: {
        starYellow() {
            return Math.ceil(this.vote / 2) 
        },
        starEmpty() {
            return  5 - (Math.ceil(this.vote / 2)) 
        },
    }
}
</script>

<template>
<div class="container">
    <div class="card border-0 bg-info">

        <div class="imgFilm ">
            <img :src="urlInitials + sizeUrl + cardSeries.poster_path" :alt="cardSeries.original_name">
        </div>

        <div class="infoFilm ">

            <p>
                <span class="fs-4 fw-bold">Title:</span> {{ cardSeries.name }} 
                <!-- {{ cardSeries.name }} -->
            </p>
    
            <p>
                <span class="fs-4 fw-bold">Original Title:</span> {{ cardSeries.original_name }}
                <!-- {{ cardSeries.original_name }} -->
    
            </p>
    
            <div>
                <CountryFlag :country='getCountryFlag(cardSeries.original_language)' size='big'/>
                
            </div>
            <div>
                    
                    <span v-for="(star) in starYellow" :key="star" >
                        <i class="fa-solid fa-star text-warning"></i>
                    </span>
    
                    <span v-for="(star) in starEmpty" :key="star" >
                        <i class="fa-solid fa-star"></i>
                    </span>
                </div>
    
            <p>
                <span class="fs-4 fw-bold">Overview:</span> {{ cardSeries.overview }}
            </p>
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