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
            <div class="header__intro"
                style="backgroundImage:url(https://image.tmdb.org/t/p/w500/t5zCBSB5xMDKcDqe91qahCOUYVV.jpg)">
                <div class="container">
                    <div class="left">
                        <a href="#">
                            <img src="https://image.tmdb.org/t/p/w500/h3hhfWdBhdb2JLMZprQ1IvBe90h.jpg" alt="포스터">
                        </a>
                    </div>
                    <div class="right">
                        <h2>프레디의 피자가게</h2>
                        <p class="desc">
                            80년대에 아이들이 실종되고 폐업한지 오래된 프레디의 피자가게 그곳의 야간 경비 알바를 하게 된 ‘마이크'는 캄캄한 어둠만이 존재하는 줄 알았던 피자가게에서 살아 움직이는
                            피자가게 마스코트 '프레디와 친구들’을 목격한다. 어딘가 기괴하고 섬뜩한 프레디와 친구들이 실체를 드러내기 시작하는데...
                        </p>
                        <p class="date">개봉 : 2023-10-25</p>
                        <p class="average">평점 : 7.9</p>
                        <div class="credits">
                            <div>
                                <img src="https://image.tmdb.org/t/p/w200/mT4nBq136sHYEJBjeoZzRGBIjxt.jpg" alt="배우1">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w200/x8tDKAgxMKwaNJSd9RB75EIJnOD.jpg" alt="배우2">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w200/lDYjEyqojUs2sF3CgdsOZ9vr2KL.jpg" alt="배우3">
                            </div>
                            <div>
                                <img src="https://image.tmdb.org/t/p/w200/51v6jsvzuAXYirIzdqcjLBp46d6.jpg" alt="배우4">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>
    <!-- //header -->
</template>

<style lang="scss">
.header__inner {
    .header__nav {
        display: flex;
        justify-content: space-between;
        align-items: center;

        h1 {
            font-size: 20px;
            padding: 5px 1rem;
            margin: 20px 10px;
        }

        nav {
            li {
                display: inline;

                a {
                    display: inline-block;
                    padding: 10px;
                }
            }
        }
    }
}

.header__intro {

    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    position: relative;
    padding: 30px;

    &::before {
        //배경 이미지 블러
        content: '';
        width: 100%;
        height: 100%;
        position: absolute;
        left: 0;
        top: 0;
        background-color: #00000032;
        backdrop-filter: blur(7px);
        z-index: 1;
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

}
</style>

