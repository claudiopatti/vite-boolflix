<script>
// import countryFlag from './countryFlag';
import CountryFlag from 'vue-country-flag-next';
import { store } from '../store.js';




export default {
    props: {
        card: Object,
        vote: Number
    },
    data() {
        return {
            // language: store.cardsFilms.original_language
            store,
            urlInitials: "https://image.tmdb.org/t/p/",
            sizeUrl: 'w342'
            
        }

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
        imgFilmSerie() {
            if (this.card.poster_path != null && this.card.poster_path != '') {
                
                return this.urlInitials + this.sizeUrl + this.card.poster_path
            } 
            else {
                return '../../img/netflixlogo.png'
            }
        },

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
                <img :src="imgFilmSerie" :alt="card.original_title">
            </div>
        
            <div class="infoFilm ">

                <p >
                    <span class="fs-4 fw-bold">Title:</span> {{ card.title }} 
                    <!-- {{ card.name }} -->
                </p>
            
                <p>
                    <span class="fs-4 fw-bold">Original Title:</span> {{ card.original_title }}
                    <!-- {{ card.original_name }} -->
            
                </p>
            
                <div>
                    <CountryFlag :country='getCountryFlag(card.original_language)' size='big'/>
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
                    <span class="fs-4 fw-bold">Overview:</span> {{ card.overview }}
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