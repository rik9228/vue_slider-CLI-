<template>
  <div id="app">
    <div class="container">
    <MainImage :mainImage="mainImage"></MainImage>
    <CurrentIndex></CurrentIndex>
    <Thumbnails></Thumbnails>
    <PrevNext></PrevNext>
    </div>
  </div>
</template>

<script>
import MainImage from './components/MainImage.vue'
import Thumbnails from './components/Thumbnails.vue'
import CurrentIndex from './components/CurrentIndex.vue'
import PrevNext from './components/PrevNext.vue'

export default {
  name: 'App',
  components: {
    MainImage,
    Thumbnails,
    CurrentIndex,
    PrevNext
  },
  data: function () {
    return {
    mainImage: {
            src: "./img/sample_01.JPG",
            alt: "sample_01.JPG",
          },
          thumbnails: [
            {
              src: "./img/sample_01.JPG",
              alt: "sample_03",
              id: 0,
            },
            {
              src: "./img/sample_02.JPG",
              alt: "sample_03",
              id: 1,
            },
            {
              src: "./img/sample_03.JPG",
              alt: "sample_03",
              id: 2,
            },
            {
              src: "./img/sample_04.JPG",
              alt: "sample_04",
              id: 3,
            },
          ],
          locations: [
            {
              id: 0,
            },
            {
              id: 1,
            },
            {
              id: 2,
            },
            {
              id: 3,
            },
          ],
          currentIndex: 0,
          currentImage: false,
    }
  },
  methods: {
     prevImage: function () {
            if (this.currentIndex == 0) {
              this.currentIndex = this.thumbnails.length;
            }
            this.currentIndex--;
            this.changeImageFunc();
          },
          nextImage: function () {
            if (this.currentIndex == this.thumbnails.length - 1) {
              this.currentIndex = 0;
              this.changeImageFunc();
              return;
            }
            this.currentIndex++;
            this.changeImageFunc();
          },
          changeMainImage: function (e) {
            const targetSrc = e.currentTarget.getAttribute("src");
            const targetNum = e.currentTarget.getAttribute("data-num");
            // 押された対象要素のdata属性値を取得してcurrentIndexに突っ込む
            this.currentIndex = targetNum;
            this.mainImage.src = targetSrc;
          },
          // 画像を変える関数
          changeImageFunc: function () {
            this.thumbnails.forEach((thumbnail) => {
              if (thumbnail.id == this.currentIndex) {
                this.mainImage.src = thumbnail.src;
              }
            });
          },
          locationChange: function (e) {
            const targetLocation = e.currentTarget.getAttribute("data-num");
            this.currentIndex = targetLocation;
            this.changeImageFunc();
          },
          timer: function () {
            setTimeout(() => {
              if (this.currentIndex == this.thumbnails.length - 1) {
                this.currentIndex = -1;
                this.changeImageFunc();
              }
              this.currentIndex++;
              this.changeImageFunc();
              this.timer();
            }, 3000);
          },
  }
}
</script>

<style>
html,
body,
div,
span,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
abbr,
address,
cite,
code,
del,
dfn,
em,
img,
ins,
kbd,
q,
samp,
small,
strong,
sub,
sup,
var,
b,
i,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
canvas,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section,
summary,
time,
mark,
audio,
video {
  margin: 0;
  padding: 0;
  border: 0;
  outline: 0;
  font-size: 100%;
  vertical-align: baseline;
  background: transparent;
}

body {
  line-height: 1;
}

article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section {
  display: block;
}

nav ul {
  list-style: none;
}

blockquote,
q {
  quotes: none;
}

blockquote:before,
blockquote:after {
  content: "";
  content: none;
}

q:before,
q:after {
  content: "";
  content: none;
}

a {
  margin: 0;
  padding: 0;
  font-size: 100%;
  vertical-align: baseline;
  background: transparent;
  text-decoration: none;
}

/* change colours to suit your needs */
ins {
  background-color: #ff9;
  color: #000;
  text-decoration: none;
}

/* change colours to suit your needs */
mark {
  background-color: #ff9;
  color: #000;
  font-style: italic;
  font-weight: bold;
}

del {
  text-decoration: line-through;
}

abbr[title],
dfn[title] {
  border-bottom: 1px dotted;
  cursor: help;
}

table {
  border-collapse: collapse;
  border-spacing: 0;
}

/* change border colour to suit your needs */
hr {
  display: block;
  height: 1px;
  border: 0;
  border-top: 1px solid #cccccc;
  margin: 1em 0;
  padding: 0;
}

input,
select {
  vertical-align: middle;
}

button {
  background-color: transparent;
  border: none;
  cursor: pointer;
  outline: none;
  padding: 0;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

* {
  list-style: none;
  text-decoration: none;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}

html,
body {
  font-size: 62.5%;
  line-height: 1;
  color: #000000;
  font-family: "Noto Sans JP", "ヒラギノ角ゴ ProN W3", "Hiragino Kaku Gothic ProN", "游ゴシック", YuGothic, "メイリオ", Meiryo, sans-serif;
}

img,
video,
object {
  display: block;
  max-width: 100%;
  height: auto;
  border: none;
  margin: 0 auto;
}

section {
  position: relative;
  z-index: 10;
}
.container {
  width: calc(100% -32px * 2);
  max-width: 980px;
  margin: 80px auto 0;
}

.mainImage {
  max-width: 650px;
}

.thumbnails {
  display: flex;
  justify-content: space-between;
  max-width: 650px;
  margin: 0 auto;
}

.locations {
  display: flex;
  justify-content: center;
  margin-top: 16px;
}

.location {
  width: 12px;
  height: 12px;
  background-color: transparent;
  border: 1px solid #dfdfdf;
  margin: 8px;
  border-radius: 100%;
  cursor: pointer;
}

.thumbnails {
  margin-top: 16px;
}

.thumbnail {
  width: 20%;
  cursor: pointer;
  transition: 0.5s;
}

.thumbnail:hover {
  opacity: 0.6;
}

.prevNext {
  display: flex;
  justify-content: center;
  margin: 32px auto 0;
  max-width: 250px;
}

.prev,
.next {
  border-radius: 4px;
  background-color: #00a4fd;
  padding: 0.5em 1em;
  transition: 0.5s;
  color: #fff;
}

.prev:hover,
.next:hover {
  opacity: 0.8;
}

.next {
  margin-left: 16px;
}

.currentImage {
  opacity: 0.5;
}

.currentLocation {
  background-color: #55c3f9;
}
</style>
