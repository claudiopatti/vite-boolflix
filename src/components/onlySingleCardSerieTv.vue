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
      changeNumberSeries() {
        const result = this.cardSeries.vote_average / 2;

        let resultFixed = result.toFixed(0)
        return resultFixed
      }

    },
}
</script>

<template>
<div>

    <div>
        <img :src="'https://image.tmdb.org/t/p/w342/' + cardSeries.poster_path" :alt="cardSeries.original_name">
    </div>
    <h2>
        {{ cardSeries.name }} 
        <!-- {{ cardSeries.name }} -->
    </h2>

    <h3>
        {{ cardSeries.original_name }}
        <!-- {{ cardSeries.original_name }} -->

    </h3>

    <div>
        {{ cardSeries.original_language }}
        <!-- {{ cardSeries.original_language }} -->
          <span :country='cardSeries.original_language'></span>:
          <span v-if="cardSeries.original_language == 'en' ">
            <img src="https://flagsapi.com/GB/flat/64.png">
          </span>
          <span v-else-if="cardSeries.original_language == 'ja'">
            <img src="https://flagsapi.com/JP/flat/64.png">
          </span>
          <span v-else-if="cardSeries.original_language != languageFilm">
            <CountryFlag :country='cardSeries.original_language' size='big'/>
          </span>
          <span v-else>
            <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAARMAAAC3CAMAAAAGjUrGAAAAllBMVEUAAAD////7///8/Pz5/f4EBAT6///5+fng4ODv7+/m5ub39/e+vr709PT4/PwvLy/Q0NCPj4+VlZXZ2dl8fHyjo6M7OzsoKCiGhobKyspzc3M1NTVDQ0NMTEzCwsLk5OQVFRWampqtra0kJCQQEBBbW1uzs7N3d3cdHR1TU1NlZWWnp6dYWFhjY2M/Pz+AgYMQFRcABwCEGdGrAAANzElEQVR4nO1dh4KisBbNpQihiYAKWLFgH9/7/597uUkozsy2t+u6MDlrYRTY5HB7EiREQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQaH7ME1i8vfPvvvLbflXYH7Vjn8bgpHjKU9Ho1F0KWM7LItkf3xxs16OcxnSwAAOjf0Dg4bjIfmyunPMPQ2pMAwNYWj8HdnJ9vj9V6JF9vWQBSC40LSBZgzYFmeHvYC/HLZ37TtkN28xUxUpGoyHwMCHlBiUFj/a8Z2/Aiumyb3NxgetRQGyArYUGi4rBnjDL+OZsJf7UMpIRQrS4yEnTIsQKDMQL17d1r8FxsnB5ZQ0uoKOZ1XU1halhu0Aq8WXUB3s5FhnLtfgrEhBQU42MRhGY2D4lj1/dXOfDG4vTXLcQMuMVCYV6MiVbGhMRnSd2dxgAGF9YE/Be3Zc6tpHTnTYeCApQQHSUWYGgQajnvtj9DjTrGU1WnJCc11vtMYAN2N2lgmMn/eaFO6ESy0Igk848QqAmhMmN6knYhag21e3+9mIIGh54AbW3Qa9oWSQnwEpQesbT/osKIRMaRWA1OC+BmjiNp8EMD7GWk1d9upWPxcX+CAhGJ9pUJTQOGEYk2XjmwYQvbrZz8TceS8lmkiHgz2t2TKYAz6gcTHEvgNtNXx1w5+IMQQfxQQFwksaAQpWbwsKeu2cmPNJX93wJ4IaH+WEi0mOHlp+4J5JCBifaEElOD1Wnj1oH+UEqbCZYFRRPSOgwHqb+NPoOyeY5A0GqAyPpECR8nyQSYemLcmV8myIPwOMUvTk1S1/HjwUhsC9G23vw7xOsFhCIBJloG87pjlSaLj+DAy6f3XLn4Z1KLhYPHjkgQbLha/JPBkOzBAbIudhcQpTtmCgOf2towxjnupYp+SdnCQjEY0MDBaf3ar0GHVq7KNHZla3r5ivkAsd8hNt2xOwp7aI+FnSlx9t3Ai4dd0wsxygII1f3fSnYeFw5wLp1H7g5HIOhFyw3AbtcFXFd1lKzGwQ4yRe97WGsnB4MAIFCVvKo8PEq/6Ew7naZGJCZ+ygs6UZFtxf3fZnYUGFOHjEa3EC4cKvxrzsYaw336ywcjKxMaax/9PTKgrnRA80ylxLi5OkAFnB9/dl9YXrGMA5WYc8nin6ygnaE9Zpi5xbnNA3pxoU3Vx5vRE3vQjA5kdlgGbW7mkayPwOD0LgbdpYDcgWPLFhD38YgiGCf5gXoFMcCNyh7RkMIO+nnAz5YAUzKAnxsfMDtq1DUfDIhG2lkfA5gQaULAF8HMgY2py/vtaqMY7lQ1ke4R1lIRrzOteQB2wBZHPhkBk/MJpTAP3OaMiF0YX81a1/EjDfQVZCrLeJYB7o3uefacZe1NZYkshI48Y2Y8oj3bbf1/B+LIfN6SJHUzLgZcYRiAB/mbvSmNDI3PM6rVHON9LyxNNXN/5JyEHML4F0ZmuivESZ4Q1QYugCh9UHYMQjk4xcEcpCNb4B5avb/ixsNZHvQibKBjifYgbSD/+HWRAIluctuWaBqL7Vox6GyHj6aGQZEwEfDYbhwuJcWLMxfwc6JFE2vrIgJrKBl+OYIglVQtkK+luRZcmLxn3MhhlRdL/lLoaWbhyjjIJ0SQ8TdoLo5vW1YFBylWFu5MA2AbJ1IQwG3PLDGzmymDVwrYAFKEZrWpec+Zf2UXdMkwyxFo29dKZm5JSziSwgBVcdnILM8wP+u0el0Zqew30URm095ARxB6kT8Yx1cWpLvxLMM2iVjnZvN2o0lWxuUTCS7Se2cWVmszUvGMnpayy/0QauDFbz0P9vAkHboAyCHhfb7jxCQVJuJIVqRB3ymxsEYDPtmKWhBUwovIfZTIy73oYoZB3L6Uhwm1DQqjw440E8y2pYosgnUpO58zDeHmCJqYfgNdU7dz2BsTpetEYUgsUZUKHIGXSdcRLvSNoqufHUqKdpoMkFhceyBVbrwa3K1SH303SRiOUI9hSrSVyExJOlRmF/Zyzh9R9o/mmhM2di77HwyKyFkTOODC3dS05mhGsP0CVobsgDFP/26qY/DyzCH/A5JgbOQXJFisw+YCkilHOLc7LCmn3u6izijWFJluDGGhxe3fJngQVueP1zHt3z8hKvPRoWITiCPrQFJ3wS2wj0E0msnFxX6XFZ9rVegHZ2uIkLwq5/lfggJQZskZNwveScOHMetc4m7WN3L2rz84EzQnF52wonLZXk7ANKCjhMTpjj2XmCk6auVmQR2aRkdwm91zX6L2EDvJJC8pULENh7ckJ7cgw5JxafKjzNz8MJQLgHazEGpK3nuKGNZTpCZoeoSIa8XAvFzBeOhykXYUkQxMy+OCyOC9l7/OomPxkm2WLBHi71J6mrGf75DNIZ89wIMH6rnsz/9Bk86y9QUPQqOj34LFS112PJCezJnKmQoAMf7NnPLNBsb75RnDJteZPtenrK0M5CSuKKk4ysPaRC53ToyEt/C5ASzP0UPGYfgJ056HswbiN+xQmzsseN2BSkAPRuqt98nC3fDVxNQ7mWlnMT4FI35ITbDp2Fc9sRzwclMVBXlczWazfB276LrNrDNpiHWDkyZJE+xHiecjXhKuP5UFnXSp2qE16T85Z0lhbZ7FKogPPuXgTDMqj6Te887V2+46GBDrQ6Y+Trrt31CaKlvPo87Kh44uWUdep5y8yLqsWQt4oSXXeFJWlBTkIZCfty+eQ/6g5uFkj/QYctgZfLr6u/+OtuWcUjlWWt5UQHQdzakWR1eMr5/BDXYRcsm0TuE2uAqVBY29TG60jM+E6bKmaxujgMhmIw9xwZZoh+pT8yjcONW3Hg2944uif3UbHxwqy88yPPVs0XJoXfvNHOv4tLRUbVD5wU/YMuHPPC88b36+x9cQA5Xjits2X57GktfwrQhqYiBG3bhV9dUWA+bE9jeDifnXRNSqa2lJGmGzr41588+kNfTYxo9JbxxbeuZYY3WrGxjNyaFPrdIN38zoWf2DUV1Yb07x0B3sBCl1IST9Mq7MCX6Cj3+Mn7m0ie8lVDh1NbYqdLN3owSW7JdpfkQtu+Nb4R0c0fc1LvNSskwfjwF3VV4X3G8E/DJAsqSNDpgUySzGpY8b2fvWFSdWM7JiT8WOmK01OtjB3Ll0e1g4gLlvXmZUwrQ2BtfmEMa5rEdcLM32gy9/UOcoKXN1nWik/DYk7WpzRzZaXIz36ySjQbx1bFCML3kjee9YjzXrujOjWmp3SzjLniUC9d4Crzuj/RD+/a9zZyGscLfuyNZsQ8RXHNUHdLkrPz2JbiYleWlusUSr5ZWw2J2h/tilXL+WaHk0l2d8+uy3EQR99z3v8+pqOQ1jah9qpxvsYvH/plikrCfKzXVhn1bXS6L5EOam+S+fYxwu0keLMXo8xtDIPs6vL06c6TiwPQsiM6WPi+KtPF7pNTdwtV7io0YjjKaEsf+Ja3+NCxBebHkrRaVmgYzY/vzvxzYc4/h/dV5VMU1oSIPtPycSXXvBS8VckNPp3N6O3diWT40kFKPsF6XqzctqQAvdRzKcx55tdfSPe7Gi/6Oteijf3GhoYWHZxozT+/LWuiBCF0GfV1/c5HDA+hDtJkoJbYyY7sxj5AY0aY707m/Z150qAVUpw20nDI5DAnu9SuGbGy4itoTBvCPZfQYsXKFmQ2EpTo5W39fu+vgltcxyu8cnYiWywtZB/Dlq8Cdvm3I6tyy0gL9ZhOXZKvYEU+hxzrGlMep0pnY106VpD/s0BO0s2a7Mva/3IX1Nu1KT+DWcpsh8v8yzV7GPxzkuOXuSH1I3YjW8iHHRGShJWp5eyE/V12UDvRj9ecy0g1/mMnazOPKw/ErW54eneqXsCsWDHNKlSr+zaNVo0H1kUFfpfYdRDLnq73Rsj3B316gDq9n4yddlID/kXE8Nu7GBK2ZGyPP5/RZ0JqTNKlBVUJEl/jSPxyCPZ+ndq1WUFjO357dXP/LGZRaNsrexUvo/N8sl3vdrvpQtQgq2IRWtNza7jHxOTwocTmlD3Ki02vTvulgjg2bcfxwGtFVY/bKpKEdfGEsxZde/HDPCYZY4ec0WlstXhpvC0vr6bf0IxtHjaygmOJdlkkSVqMxxuPoRzfcSVLxwIYk2y5XThMk7H1OFuvIsQWSvFZv/jvapRyvqxFP50N6Yw6VknAxcKcE2f1oTNi/KpMJuQbPqWqse4LviveHUYkie8Q/s0e/QGYuEhUjuXQiD5Qovs/nc+cs5VLR2Z70pYObjLJM9zYPLMHfx5mPYaus+sZP1zfn5zyK4RleA4hHM7bZ3CZjJ3xxFn3KgpRTLkpiUnctgjLX/QhOw/oiWTV0IYwvHwEuoOckPX1kC5x3VrIo3dfrMT5Zbe6XgLNiScHwaBJCLp6G4MZBYtPuXcmaDJpSt6Pmf8YuwwnmmyqMI6Xbtkmnfz40H8QJt5lDZKpSzfrRSxMya8ygnszUi6kql7zV3/V1fjWxLuQQXiczHYHCno5I//HcCYWbVlMvCG5A76HFQb7fFrMOhezNTBxBeioQCE5/EY3GCnZcJofyYiFcp2vN+1FdOIXv/WzmeuLDqv7PsK7xnRtqvAnuMZ2nKW/vWDgIOdxQTzsrtbUOE6q1OS3ujIphcBV1bfuojGppvkb9oQfuI2yuBx2vhrZbv/vTKGp1oWtSYf9jYKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgsJ38D8HTLVz00Q28gAAAABJRU5ErkJggg==" alt="">
          </span>




        <!-- <CountryFlag :country='cardSeries.original_language' size='big'/> -->
        <!-- <h4 v-if="cardSeriesLaunguage === en" > 
            <img src="https://flagsapi.com/GB/flat/64.png">
        </h4> -->



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

</div>

    
</template>

<style lang="scss" scoped>

</style>