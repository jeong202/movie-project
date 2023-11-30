<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <div class="header__nav">
                <h1 class="text">
                    CINEMA + MOVIE
                </h1>
                <nav>
                    <ul>
                        <li><a href="#">어떤 영화 Top10</a></li>
                        <li><a href="#">무슨 영화 Top10</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>
    <!-- //header -->

    <main id="main" role="main">
        <div class="detail__intro">
            <DetailIntro v-if="movieBasic" :movieBasic="movieBasic" />
            <DetailInfo v-if="movieInfo" :movieInfo="movieInfo" />
            <DetailReviwe v-if="movieReviwe" :movie="movieReviwe" />
            <DetailCredits v-if="DetailCredits" :movie="DetailCredits" />
        </div>

    </main>
</template>

<script>
import { ref, onMounted } from "vue"
import { useRoute } from "vue-router"
import axios from 'axios';

import DetailIntro from "../components/detail/DetailIntro.vue"
import DetailInfo from "../components/detail/DetailInfo.vue"
import DetailReviwe from "../components/detail/DetailReviwe.vue"
import DetailCredits from "../components/detail/DetailCredits.vue"

export default {
    name: "MovieDetailPage",

    components: {
        DetailIntro,
        DetailInfo,
        DetailReviwe,
        DetailCredits,
    },

    setup() {
        const movieBasic = ref(null)
        // const movieInfo = ref(null)
        // const movieReviwe = ref(null)
        // const movieCredits = ref(null)
        const route = useRoute();

        onMounted(async () => {
            const movieId = route.params.movieId
            const apiKey = import.meta.env.VITE_API_KEY;
            const language = "ko-KR"

            try {
                const resMovieBasic = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`)
                movieBasic.value = resMovieBasic.data;
                console.log(resMovieBasic.data)

                // const resMovieInfo = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`)
                // movieInfo.value = resMovieInfo.data;
                // console.log(resMovieInfo.data)

                // const resMovieReviwe = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`)
                // movieReviwe.value = resMovieReviwe.data;
                // console.log(resMovieReviwe.data)

                // const resMovieCredits = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`)
                // movieCredits.value = resMovieCredits.data;
                // console.log(resMovieCredits.data)

            } catch (err) {
                console.log(err)
            }
        });
        return { movieBasic }
    }
}

</script>