<template>
  <div class="home">
    <div class="myName d-flex flex-column justify-content-center">
      <h1>Tetsuo Hirota</h1>
      <h2>Web Engineer</h2>
    </div>

    <section id="aboutMe">

      <div class="title" id="title-aboutMe">About Me</div>

      <div class="body">
        <div class="profile-1 d-flex flex-column flex-md-row align-items-center justify-content-center">
          <img src="./../assets/me.jpg" alt="">
          <div class="comment">
            私はWebフロントエンドエンジニアです。UI/UXの領域に知見があり、日々研究に励んでいます。趣味はギター、映画鑑賞。
          </div>
        </div>
        <div class="profile-2">
          <p>生年月日：1995 年 6 月 27日</p>
          <p>職業：大学生</p>
          <p>所属：慶應義塾大学 理工学部</p>
          <p>スキル：HTML, CSS, Javascript, Typescript, Vue, Angular</p>
        </div>
      </div>

      
    </section>

    <section id="myWork">

      <div class="title" id="title-myWork">My Work</div>

      <div class="body">

        <div class="item mjapp">
          <div class="card">
            <h4>麻雀成績管理</h4>
            <div class="bg"><img src="./../assets/mjapp-thum.jpg" alt=""></div>
            <button @click="showModalMjapp = true"></button>
          </div>
          <transition name="modal">
            <div class="modal-bg" v-if="showModalMjapp" @click="showModalMjapp = false">
              <div class="modal-content  d-flex flex-column flex-md-row align-items-center justify-content-center" @click.stop>
                <div class="close" @click="showModalMjapp = false">✖</div>
                <img src="./../assets/mjapp.png" alt="">
                <div class="introduction">
                  <h2>麻雀成績管理アプリ</h2>
                  <p>
                    麻雀の成績を記録、共有するアプリケーションです。
                    統計をグラフで表示したり、対戦中のフレンドとのリアルタイムデータ同期機能を備えています。
                    現在UIを改善した新しいバージョンを開発中です。
                  </p>
                  <div class="btns">
                    <b-btn href="https://mj-app-pwa.web.app/" target="_blank" variant="outline-light">アプリ開始</b-btn>
                    <b-btn href="https://github.com/TetsuoHirota/mjapp" target="_blank" variant="outline-light">Github</b-btn>
                  </div>
                </div>
              </div>
            </div>
          </transition>
        </div>

        <div class="item mjapp">
          <div class="card">
            <h4>麻雀成績管理 Ver.2</h4>
            <div class="bg"><img src="./../assets/mjapp-2-thum.jpg" alt=""></div>
            <button @click="showModalMjapp2 = true"></button>
          </div>
          <transition name="modal">
            <div class="modal-bg" v-if="showModalMjapp2" @click="showModalMjapp2 = false">
              <div class="modal-content  d-flex flex-column flex-md-row align-items-center justify-content-center" @click.stop>
                <div class="close" @click="showModalMjapp2 = false">✖</div>
                <img src="./../assets/mjapp-2.png" alt="">
                <div class="introduction">
                  <h2>麻雀成績管理アプリ Ver.2（製作中）</h2>
                  <p>
                    麻雀成績管理アプリの改良版です。ゲストログインやGoogle認証の実装、UIの改善を行っています。
                  </p>
                  <div class="btns">
                    <b-btn href="https://mj-app-2.web.app/" target="_blank" variant="outline-light">アプリ開始</b-btn>
                    <b-btn href="https://github.com/TetsuoHirota/mj-app-2" target="_blank" variant="outline-light">Github</b-btn>
                  </div>
                </div>
              </div>
            </div>
          </transition>
        </div>

      </div>
    </section>

    <section id="contact">
      <h1>Contact</h1>

      <div class="contact__btns">
        <b-btn variant="light" href="mailto:namao0627@gmail.com">
          <i class="fas fa-envelope"></i>
        </b-btn>
        <b-btn variant="light" href="https://twitter.com/namao0627" target="_blank">
          <i class="fab fa-twitter"></i>
        </b-btn>
      </div>

    </section>

  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component({
  components: {}
})
export default class Home extends Vue {
  showModalMjapp = false
  showModalMjapp2 = false
  mounted() {
    window.addEventListener("scroll", () => {
      const height = window.innerHeight
      const contents = [
        (document.getElementById('title-aboutMe') as HTMLElement),
        (document.getElementById('title-myWork') as HTMLElement)
      ]
      for (const content of contents) {
        if (height - 200 > content.getBoundingClientRect().top) {
          content.classList.add('fade-in')
        } else {
          content.classList.remove('fade-in')
        }

      }
    })
  }

  open(id: string) {
    (document.getElementById(id) as HTMLElement).classList.add('open')
  }

}
</script>

<style lang="scss" scoped>

// メディアクエリ
$tab: 959px; // タブレット
$sp: 559px;  // スマホ

@mixin tab {
  @media (max-width: ($tab)) {
    @content;
  }
}
@mixin sp {
  @media (max-width: ($sp)) {
    @content;
  }
}

.myName {
  height: 720px;
  @include sp {
    height: 660px;
  }
  h1, h2 {
    min-width: 0;
  }
}

section {
  position: relative;
  padding: 0 50px;
  .body {
    padding: 220px 20px 80px;
    @include sp {
      padding: 100px 10px;
    }
  }
}

.title {
  position: absolute;
  top: 0;
  font-size: 150px;
  color: rgba(0,0,0,.3);
  transition: 1s;
  opacity: 0;
  transform: translateX(-80px);
  @include tab {
    font-size: 100px;
  }
  @include sp {
    font-size: 50px;
  }
}

.fade-in {
  opacity: 1;
  transform: translateX(0);
}

.name {
  width: 400px;
  margin: 0 auto;
}

#aboutMe {
  .profile-1 {
    img {
      z-index: 10;
      margin: 60px 80px;
      height: 200px;
      border-radius: 5px;
      box-shadow: 2px 2px 10px 4px grey;
      border: 1px solid white;
      transition: .2s;
      &:hover {
        transform: scale(1.02);
      }
      @include sp {
        margin: 0;
      }
    }
    .comment {
      margin: 60px 0;
      max-width: 400px;
    }
  }
  .profile-2 {
    margin: 100px 0;
    @include sp {
      margin: 30px 0;
    }
  }
}

#myWork {
  .body {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    .item {
      .card {
        display: flex;
        justify-content: center;
        position: relative;
        transition: .5s;
        margin: 20px;
        height: 300px;
        width: 200px;
        box-shadow: 0px 0px 20px 1px grey;
        padding: 10px;
        border-radius: 10px;
        overflow: hidden;
        &::after {
          content: "";
          position: absolute;
          top: 0;
          left: 0;
          height: 100%;
          width: 100%;
          background: rgba(0,0,0,.4);
          opacity: 0;
          transition: .5s;
        }
        .bg {
          position: absolute;
          height: 100%;
          width: 100%;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          img {
            transition: .5s;
            height: 100%;
            width: 100%;
            object-fit: cover;
          }
        }
        button {
          z-index: 10;
          position: absolute;
          top: 0;
          left: 0;
          background: transparent;
          outline: 0;
          border: none;
          height: 100%;
          width: 100%;
          cursor: pointer;
        }
        h4 {
          color: white;
          font-weight: bold;
          opacity: 0;
          transition: .5s;
          z-index: 10;
        }

        &:hover {
          transform: scale(1.05);
          &::after {
            opacity: 1;
          }
          h4 {
            opacity: 1;
          }
          .bg {
            img {
              transform: scale(1.1);
            }
          }
        }
      }
      .modal-bg {
        position: fixed;
        top: 0;
        left: 0;
        height: 100vh;
        width: 100vw;
        background: rgba(0,0,0,.4);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 100;
        .modal-content {
          width: auto;
          background: #660000;
          color: white;
          padding: 30px;
          position: relative;
          .close {
            position: absolute;
            top: 20px;
            right: 20px;
            color: white;
            cursor: pointer;
          }
          .introduction {
            max-width: 300px;
            margin: 0 30px;
            h2 {
              margin: 20px 0;
            }
            p {
              opacity: 0.7;
            }
            .btns {
              a {
                margin: 10px;
                width: 200px;
              }
            }
          }
          @include sp {
            transform: scale(.7);
          }
        }
      }
    }
  }

  .mjapp {
    .modal-content {
      img {
        width: 200px;
        border-radius: 10px;
      }
    }
  }

}


#contact {
  padding-bottom: 60px;
  .contact__btns {
    a {
      margin: 0 10px;
      transition: 0.2s;
      i {
        font-size: 28px;
      }
      &:hover {
        transform: scale(1.2);;
      }
    }
  }
}

// トランジション
.modal {
  &-enter-active {
    animation: modal-in .3s;
  }
  &-leave-active {
    animation: modal-out .3s;
  }
  @keyframes modal-in {
    0% {
      transform: scale(1);
    }
    50% {
      transform: scale(1.1);
    }
    100% {
      transform: scale(1);
    }
  }
  @keyframes modal-out {
    0% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }
}
</style>
