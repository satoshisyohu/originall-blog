<template>
  <div>
    <!-- 詳細ページのコンテンツ -->
    <!--    <h1>Item Detail</h1>-->
    <!--    <p>ID: {{ $route.params.id }}</p>-->

    <!-- 他のコンテンツをここに追加 -->
  </div>
  <div class="detail">
    <div class="content-box">
      <div class="article-box">
        <h1 v-if="article">
          <div v-if="article.title" class="title">
            {{ article.title }}
          </div>
          <div v-if="article.publishedAt" class="publishedAt">
            {{ formatDate(article.publishedAt) }}
          </div>
          <div v-html="article.content" class="main-contents"></div>
        </h1>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import {ar} from "vuetify/locale";
import dayjs from "dayjs";

export default {
  // 詳細ページのロジックをここに追加
  name: 'DetailView',
  computed: {
    ar() {
      return ar
    }
  },
  data() {
    return {
      article: [],
    };
  },
  mounted() {
    const id = this.$route.params.id
    this.get_article(id);
  },
  methods: {
    get_article(id) {
      const headers = {
        "Content-Type": "application/json",
      }
      const body = {
        "articleId": id
      }
      // const url = 'http://localhost:8080/v1/article/retrieve-detail'
      const url = 'https://original-blog-y3raiwisja-uc.a.run.app/v1/article/retrieve-detail'
      axios.post(url, body,{headers: headers}).then(response => {
        if (response.status === 200) {
          console.log(response.data)
          this.article = response.data
          console.log(this.article)
        }
      }).catch(error => {
        console.log(error)
      });
    },
    formatDate(dateString) {
      console.log(dateString)
      return dayjs(dateString).format('YYYY-MM-DD');
    },
  }
};
</script>

<style>
@media (min-width: 1024px) {
  .detail {
    width: 800px;
    margin: 0 auto;
    padding-top: 20px;
    padding-right: 10px;
    padding-left: 10px;
  }

  .publishedAt {
    /*padding-top: 20px;*/
    /*padding-bottom: 20px;*/
    font-size: 13px;
  }

  .main-contents {
    padding-top: 20px;
    padding-bottom: 20px;
    font-size: 17px;
  }


}
</style>