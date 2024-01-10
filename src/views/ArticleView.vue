<script>
import axios from 'axios';
import dayjs from "dayjs";
import router from "@/router";

export default {
  name: 'ArticleView',
  data() {
    return {
      articleList: [],

    };
  },
  mounted() {
    this.get_article();
  },
  methods: {
    get_article() {
      const headers = {
        "Content-Type": "application/json",
      }
      // const url = 'http://localhost:8080/v1/article/retrieve-all'
      const url = 'https://original-blog-y3raiwisja-uc.a.run.app/v1/article/retrieve-all'
      axios.post(url, {headers: headers}).then(response => {
        if (response.status === 200) {
          console.log(response.data)
          this.articleList = response.data.contents
          console.log(this.articleList)
        }
      }).catch(error => {
        console.log(error)
      });
    },
    formatDate(dateString) {
      return dayjs(dateString).format('YYYY-MM-DD');
    },
    truncateString(str) {
      const maxLength = 50; // 最大文字数
      if (str.length > maxLength) {
        return str.slice(0, maxLength) + '...'; // 指定の文字数に切り詰めて末尾に省略記号を追加
      } else {
        return str; // 指定の文字数未満の場合はそのまま返す
      }
    },
    goToDetail(value) {
      // IDに基づいてページ遷移などの処理を行う
      // ここでは単純にログにIDを表示するだけの例を示します
      console.log('Clicked ID:', value.id);
      // ページ遷移の処理などを記述
      router.push(`/detail/${value.id}`); // Vue Routerを使用してページ遷移する場合の例
    }

  }
};


</script>

<template>
  <div class="about">
    <h2>
      #Article
    </h2>
    <div class="content-box">
      <div class="article-box">
        <ul>
          <li v-for="(value) in articleList" :key="value.id" @click="goToDetail(value) ">
            <v-card
                class="mx-auto my-4"
                :title="value.title"
                :subtitle="formatDate(value.publishedAt)"
                :text="truncateString(value.description)"
                variant="tonal"
                link>
            </v-card>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>


<style>
@media (min-width: 1024px) {

  div{
    font-family:'ui-monospace,SFMono-Regular,Menlo,Monaco,Consolas,Liberation Mono,Courier New,monospace', 'Noto Sans JP', sans-serif;
  }

  .about {
    width: 800px;
    margin: 0 auto;
    padding-top: 20px;
    padding-right: 10px;
    padding-left: 10px;
  }

  li {
    list-style: none;
  }


}
</style>
