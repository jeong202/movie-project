<script setup>
// import { ref, onMounted } from 'vue'
// import axios from 'axios'



// const movies = ref([]);
// const searchKeyword = ref('');

// let url = 'https://api.themoviedb.org/3/movie/popular';
// const fetchMovies = async (category) => {
//   switch (category) {
//     case 'now_playing':
//       url = 'https://api.themoviedb.org/3/movie/now_playing';
//       break;

//     case 'popular':
//       url = 'https://api.themoviedb.org/3/movie/popular';
//       break;

//     case 'upcoming':
//       url = 'https://api.themoviedb.org/3/movie/upcoming';
//       break;

//     case 'top_rated':
//       url = 'https://api.themoviedb.org/3/movie//top_rated';
//       break;
//   }

//   try {
//     const response = await axios.get(url, {
//       params: {
//         api_key: 'dc1b4f859c38448e3c7d03daf3da75ec',
//         language: 'ko-KR',
//         page: 1
//       }
//     });

//     movies.value = response.data.results;
//     console.log(movies);

//   } catch (err) {
//     console.log(err);
//   }
// };

// const searchMovies = async () => {
//   try {
//     const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
//       params: {
//         api_key: 'dc1b4f859c38448e3c7d03daf3da75ec',
//         language: 'ko-KR',
//         query: searchKeyword.value,
//         page: 1
//       }
//     });
//     movies.value = response.data.results;
//     console.log(movies);

//   } catch (err) {
//     console.log(err);
//   }
// };

// fetchMovies('now_playing'); // 최초 렌더링 시 popular 카테고리를 불러오도록 설정

// onMounted(async () => {
//   // 초기 페이지 로딩 시 최신 영화를 가져옴
//   await fetchMovies('now_playing');
// });
</script>

<template>
  <HeaderSection />
  <!-- //header -->

  <main id="main" role="main">
    <div class="container">
      <div class="movie__inner">
        <MovieSearch @onSearch="search" />
        <MovieTag @onSearch="tags" />
        <MovieCont />

      </div>
    </div>
  </main>
  <!-- //main -->

  <FooterSection />
  <!-- //footer -->
</template>

<script>
import HeaderSection from '@/components/section/HeaderSection.vue';
import FooterSection from '@/components/section/FooterSection.vue';

import MovieSearch from '@/components/contents/movieSearch.vue';
import MovieTag from '@/components/contents/movieTag.vue';
import MovieCont from '@/components/contents/movieCont.vue';

export default {
  name: "MovieHomePage",
  components: {
    HeaderSection,
    FooterSection,
    MovieSearch,
    MovieTag,
    MovieCont,
  },
  data() {
    return {
      movies: [],
    }
  },
  methods: {
    async search(query) {
      try {
        const response = fetch(`https://api.themoviedb.org/3/search/movie?api_key=dc1b4f859c38448e3c7d03daf3da75ec&language:ko-KR&query=${query}`)
        const result = (await response).json();
        console.log(result)
      } catch (error) {
        console.log(error)
      }
    },
    async tag(query) {
      try {
        const response = fetch(`https://api.themoviedb.org/3/search/movie?api_key=dc1b4f859c38448e3c7d03daf3da75ec&language:ko-KR&query=${query}`)
        const result = (await response).json();
        console.log(result)
      } catch (error) {
        console.log(error)
      }
    },
    async content(query) {
      try {
        const response = fetch(`https://api.themoviedb.org/3/search/movie?api_key=dc1b4f859c38448e3c7d03daf3da75ec&language:ko-KR&query=${query}`)
        const result = (await response).json();
        console.log(result)
      } catch (error) {
        console.log(error)
      }
    },
  },
}
</script>

<style lang="scss">
.movie__search {
  margin: 50px 0 20px;
  position: relative;

  input {
    border: 1px solid var(--white);
    padding: 1rem 2rem;
    width: 100%;
    border-radius: 50px;
  }

  button {
    position: absolute;
    right: 60px;
    top: 9px;
    width: 85px;
    height: 34px;
    background-color: var(--black);
    color: var(--white);
    border-radius: 10px;
    cursor: pointer;

    &:hover {
      background-color: var(--black300);
    }
  }
}

.movie__tag {
  ul {
    display: flex;

    li {
      a {
        border: 1px solid var(--white);
        padding: 0.5rem 1.3rem;
        display: inline-block;
        border-radius: 50px;
        margin-bottom: 20px;
        margin-right: 10px;
        margin-top: 20px;

        &:hover {
          background-color: var(--white);
          color: var(--black);
        }
      }
    }
  }
}

.movie__cont {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;

  .movie {
    width: 24%;
    margin-bottom: 1.5%;
    background-color: #ccc;
  }

}
</style>
