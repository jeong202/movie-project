<template>
    <div class="detail__intro" :style="{
        backgroundImage: 'url(https://image.tmdb.org/t/p/w500/' + movieBasic.backdrop_path + ')'
    }">
        <div class="container">
            <div class="left play__icon">
                <a href="#">
                    <img :src="'https://image.tmdb.org/t/p/w500/' + movieBasic.poster_path" :alt="movieBasic.title">
                </a>
            </div>
            <div class="right">
                <h2>{{ movieBasic.title }}{{ movieBasic.original_title }}</h2>
                <p>{{ movieBasic.overview }}</p>
                <p>기본 언어 : {{ movieBasic.original_language }}</p>
                <p>인기 : {{ movieBasic.popularity }}</p>
                <p>개봉 날짜 : {{ movieBasic.release_date }}</p>
                <p>영화 시간 : {{ movieBasic.runtime }}분</p>
                <p class="desc">{{ movieBasic.overview }}</p>
                <div>장르 :
                    <span v-for="genre in movieBasic.genres" :key="genre.id" class="genre">{{ genre.name }}</span>

                </div>
                <div class="credits">
                    <!-- <div>
                        <img src="https://image.tmdb.org/t/p/w200/mT4nBq136sHYEJBjeoZzRGBIjxt.jpg" alt="배우1">
                    </div> -->
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: {
        movieBasic: {

        }
    }
}
</script>
<style>
.detail__intro {

    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    position: relative;
    padding: 10px;

    &::before {
        content: '';
        width: 100%;
        height: 100%;
        position: absolute;
        left: 0;
        top: 0;
        background-color: #00000032;
        backdrop-filter: blur(5px);
        z-index: 1;
    }
}

.container {
    display: flex;
    justify-content: space-between;
    position: relative;
    z-index: 10;

    .left {
        width: 350px;

    }

    .right {
        width: calc(100% - 390px);

        h2 {
            font-size: 30px;
            margin-bottom: 10px;
        }

        .desc {
            margin-bottom: 10px;
        }

        .credits {
            width: 100%;
            display: flex;

            img {
                width: 65%;
                margin: 10px;
            }
        }
    }
}
</style>