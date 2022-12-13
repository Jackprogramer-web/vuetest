<template>
  <body>
    <div class="inner">
      <ul class="news-theme">
        <li @click="[getEconomy(), changeClass()]" class="btn">경제</li>
        <li @click="[getLiving(), changeClass()]" class="btn">리빙</li>
        <li>엔터</li>
      </ul>

      <div class="news-list-wrap">
        <ul class="news-list">
          <li class="news-item" :key="list.id" v-for="list in lists">
            <a href="#" class="news-img-wrap">
              <img :src="list.img_url" alt="" />
            </a>

            <a href="#" class="news-info">
              <em class="news-category">{{ list.category }}</em>
              <strong class="news-title">{{ list.title }}</strong>
              <p class="news-text">
                {{ list.text }}
              </p>
              <span class="news-date"> {{ list.date }}</span>
            </a>
          </li>
        </ul>
      </div>
    </div>
  </body>
</template>

<script>
import axios from "axios";

export default {
  name: "newsData",
  components: {},
  data() {
    return {
      lists: {},
    };
  },
  setup() {},
  created() {},
  mounted() {},
  unmounted() {},
  methods: {
    getLiving() {
      const vm = this;
      axios
        .get("http://localhost:4000/news/living")
        .then(function (response) {
          vm.lists = response.data;
        })
        .catch(function (error) {
          console.log(error);
        });
    },
    getEconomy() {
      const vm = this;
      axios
        .get("http://localhost:4000/news/economy")
        .then(function (response) {
          vm.lists = response.data;
        })
        .catch(function (error) {
          console.log(error);
        });
    },
    changeClass() {
      const btns = document.querySelectorAll(".btn");
      btns.forEach((btn, index) => {
        btn.classList.add("news-on");
      });
      console.log(this);
    },
  },

  created() {
    const vm = this;
    axios
      .get("http://localhost:4000/news/economy")
      .then(function (response) {
        vm.lists = response.data;
      })
      .catch(function (error) {
        console.log(error);
      });
  },
};
</script>

<style scoped>
/*공통 영역*/
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

a {
  text-decoration: none;
}

ul,
li,
ol {
  list-style: none;
}

body {
  background: #ededed;
}

/* 박스영역 */
.inner {
  width: 1100px;
  margin: auto;
  padding: 10px;
  position: relative;
}

/*상단버튼*/
.news-theme {
  display: flex;
  width: 800px;
}

.news-theme li {
  height: auto;
  width: 100px;
  cursor: pointer;
  padding: 10px;
  margin-right: 20px;
  border-radius: 20px;
  box-shadow: 0px 0px 3px 0.4px;
}

.news-on {
  background: #0f4c81;
  color: #fff;
  box-shadow: 0px 0px 3px 0.4px;
}

/*news카드*/
.news-list-wrap {
  margin-top: 10px;
  width: 100%;
  height: auto;
  padding: 25px;
  background: #fff;
  border-radius: 35px;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
}

.news-list {
  width: 100%;
  height: 100%;
}

.news-item {
  width: 100%;
  height: 350px;
  position: relative;
  display: flex;
}
/*news img*/
.news-item .news-img-wrap {
  width: 450px;
  height: 300px;
  position: absolute;
  left: 0px;
  top: 10px;
}

.news-img-wrap img {
  width: 450px;
  height: 300px;
  transition: 0.4s;
}

.news-img-wrap img:hover {
  transform: scale(105%);
}

/*news info*/
.news-info {
  width: 500px;
  height: 100%;
  position: absolute;
  left: 500px;
  display: flex;
  flex-direction: column;
  text-align: left;
}
/*news category*/
.news-category {
  color: red;
  padding: 10px;
}

.news-category:hover {
  font-weight: bold;
}

/*news-title*/
.news-title {
  color: #000;
  width: auto;
  padding-left: 10px;
  display: inline;
}

.news-title::after {
  content: "";
  display: block;
  width: 0px;
  height: 1px;
  background: #000;
  transition: 0.5s;
}

.news-title:hover::after {
  width: 100%;
}

/*news-text*/
.news-text {
  padding: 10px 0px 0px 10px;
  color: #404040;
}

/*news-date*/
.news-date {
  padding: 10px 0px 0px 10px;
}
</style>
