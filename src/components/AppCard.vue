<script>
import {store} from "../store";

export default {
    props: {
        movie :Object
    },  
    name: "AppCard",
    data() {
        return {
            store
        }
    },
    methods: {
        switchLanguage(lang) {
            switch(lang) {
                case "en":
                    return "GB";
                case "ja":
                    return "JP";
                case "ko":
                    return "KR";
                case "cs":
                    return "CZ";
            }
        return lang.toUpperCase();
        }
    }
}
</script>

<template>
    <div class="ms_card">
        <img v-if="movie.poster_path === null" class="img-fluid h-100 card-img" src="https://www.deckchaircinema.com/template_1/img/default-movie-portrait.jpg" alt="default">
        <img v-else :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path" class="card-img img-fluid h-100" alt="">
        <div class="ms_info-section card-img-overlay">
            <h5 class="card-title">{{ movie.title }}</h5>
            <p class="card-text">{{ movie.original_title }}</p>
            <img :src="'https://purecatamphetamine.github.io/country-flag-icons/3x2/' +switchLanguage(movie.original_language) + '.svg'" alt="language" class="ms_language">
            <!-- <p class="card-text"><small>{{ movie.original_language }}</small></p> -->
            <p class="card-text"><small>{{ movie.vote_average }}</small></p>
        </div>
    </div>
</template>

<style scoped lang="scss">
.ms_info-section {
    opacity: 0;
    background-color: rgba($color: #00000076, $alpha: .6);
    transition: 1s;
}
.ms_card:hover .ms_info-section{
    opacity: 1;
}

.ms_language {
    height: 20px;
}

</style>